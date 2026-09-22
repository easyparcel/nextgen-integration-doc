# EasyParcel On-Demand API — Integration Guide

On-demand (point-to-point) delivery books a rider to collect from one location and deliver straight
to another, usually within the hour. Unlike standard shipping it is driven by **coordinates**, not
postcodes, and the booking stays live — the driver, the status and the tracking link all update
after the order is placed.

This guide covers every on-demand action on the EasyParcel Connect API. It is written for
developers building an integration; you need an EasyParcel account and its **API key**.

---

## 1. Before you start

On-demand is available to accounts in **Malaysia (MY)** and **Singapore (SG)**. Your account must
hold enough credit to cover the delivery at the moment you place the order.

You also need a **latitude and longitude for every pickup and drop-off point**. On-demand books by
coordinate, not by postcode, so resolve your addresses to coordinates with the mapping provider of
your choice (Google Maps, OpenStreetMap, your platform's own geocoder) before you call the API.

### The typical flow

```
1. OndemandQuotation      get the couriers and prices for that route
2. OndemandPlaceOrder     book one of them  -> order_number
3. OndemandOrderDetails   poll for driver, status and tracking
4. OndemandCancelOrder    cancel while it is still cancellable
```

Quoting is free and is not charged against your wallet. Only step 2 charges the account.

---

## 2. Making a request

### Base URL

One host per country, matching the country your EasyParcel account is registered in:

| Country | Base URL |
|---|---|
| Malaysia | `https://connect.easyparcel.my` |
| Singapore | `https://connect.easyparcel.sg` |

The action goes in the `ac` query parameter:

```
POST https://connect.easyparcel.my/?ac=OndemandQuotation
```

### Request format

On-demand actions take a **JSON body** — not form-encoded data. Waypoints and packages are nested
objects, so a form encoding cannot express them.

```http
POST /?ac=OndemandQuotation HTTP/1.1
Host: connect.easyparcel.my
Content-Type: application/json

{ "api": "YOUR_API_KEY", "waypoint": [ ... ] }
```

Every action takes `api` — your EasyParcel API key — as a top-level field in the body. There is no
separate header or bearer token.


### Response envelope

Every action replies with the same envelope. Read the outcome from the body, not from the HTTP
status code — a failed operation still comes back as a normal 200 response:

```json
{
  "api_status": "Success",
  "error_code": "0",
  "error_remark": "",
  "result": { }
}
```

| Field | Meaning |
|---|---|
| `api_status` | `Success` when the request was authenticated and understood, `Error` otherwise |
| `error_code` | `0` on success. Anything else is a failure — read `error_remark` |
| `error_remark` | Human-readable reason, safe to surface to a merchant |
| `result` | The payload. Shape depends on the action |

**Check `error_code`, not `api_status`.** A request can authenticate fine (`api_status: "Success"`)
and still fail the operation — a cancellation refused because a driver already collected the parcel
comes back as `api_status: "Success"`, `error_code: "-1"` with the reason in `error_remark`.

`OndemandPlaceOrder` is the exception to the envelope: it returns its fields at the top level rather
than under `result`. See §4.

---

## 3. `OndemandQuotation` — what will it cost

Quote a route before booking it. The quote tells you which couriers can serve it, what vehicle each
would send, and the price.

### Request

| Field | Required | Notes |
|---|---|---|
| `api` | yes | your API key |
| `waypoint` | yes | array, at least one `pickup` and one `dropoff`, **in visiting order** |
| `pickup_date` | no | `YYYY-MM-DD`. Omit for "as soon as possible" |
| `pickup_time` | no | `HH:MM:SS`, 24-hour, in the pickup location's local time |

Each `waypoint` item:

| Field | Required | Notes |
|---|---|---|
| `type` | yes | `pickup` or `dropoff` |
| `latitude` | yes | decimal degrees |
| `longitude` | yes | decimal degrees |
| `address` | no | the human-readable address for that point |

```json
{
  "api": "YOUR_API_KEY",
  "pickup_date": "2026-09-12",
  "pickup_time": "14:30:00",
  "waypoint": [
    { "type": "pickup",  "latitude": 3.1421, "longitude": 101.6871, "address": "12 Jalan Example, Kuala Lumpur" },
    { "type": "dropoff", "latitude": 3.1580, "longitude": 101.7120, "address": "88 Jalan Sample, Kuala Lumpur" }
  ]
}
```

### Response

`result` is an array of quotes, one per courier service. An empty array means no courier serves that
route at that time — a common and legitimate answer, not an error.

```json
{
  "api_status": "Success",
  "error_code": "0",
  "result": [
    {
      "service_id": "EP-CS0K3M2P",
      "courier": "Lalamove",
      "courier_image": "https://.../lalamove.png",
      "transportation_type": "Motorcycle",
      "parcel_type_support": "Document, Parcel",
      "max_weight": "20 kg",
      "max_dimension": "40 x 40 x 40 cm",
      "estimate_durations": "30 mins",
      "estimate_price": 9.8,
      "currency": "MYR"
    }
  ]
}
```

| Field | Notes |
|---|---|
| `service_id` | **Opaque.** Pass it back to `OndemandPlaceOrder` verbatim. Do not parse, trim or rebuild it — the format varies by account |
| `courier` | Courier's display name |
| `courier_image` | Absolute URL to the courier logo |
| `transportation_type` | The vehicle that would be dispatched — Motorcycle, Car, Van … |
| `parcel_type_support` | What the vehicle accepts |
| `max_weight` / `max_dimension` | Capacity of that vehicle. Check your parcel against these before booking |
| `estimate_durations` | Courier's own estimate. May contain `<br/>` between lines |
| `estimate_price` | Total payable, tax included, in `currency` |
| `currency` | ISO currency code |
| `addon_sms_notification_price` | Tracking sms charges if enabled |
| `addon_email_notification_price` | Tracking email charges if enabled |
| `addon_whatsapp_notification_price` | Tracking whatsapp charges if enabled |


A quote is an estimate at that moment. Prices move with demand and distance; re-quote if the user
sits on the screen before booking.

**Linked courier accounts.** If your EasyParcel account has its own courier account linked, those
quotes carry extra pricing fields — `is_byoc: true`, `byoc_connection_label` (which linked account it
is), `shipment_price` (billed by the courier to your own account), and `byoc_charges` /
`byoc_charges_tax` (the EasyParcel platform fee, the part charged to your EasyParcel credit). Treat
all of these as optional: they are absent on ordinary quotes.

---

## 4. `OndemandPlaceOrder` — book it

Charges the account and dispatches the booking to the courier.

### Request

| Field | Required | Notes |
|---|---|---|
| `api` | yes | your API key |
| `service_id` | yes | exactly as returned by `OndemandQuotation` |
| `waypoint` | yes | array — same points as the quote, now with contacts and parcels |
| `pickup_date` | no | `YYYY-MM-DD` |
| `pickup_time` | no | `HH:MM:SS` |
| `coupon_codes` | no | array of coupon code strings |
| `addon_tracking_sms_enabled` | no | Enable tracking sms |
| `addon_tracking_email_enabled` | no | Enable tracking email |
| `addon_tracking_whatsapp_enabled` | no | Enable tracking whatsapp |


Each `waypoint` item:

| Field | Required | Notes |
|---|---|---|
| `type` | yes | `pickup` or `dropoff` |
| `latitude` / `longitude` | yes | decimal degrees |
| `address` | yes | full address shown to the rider |
| `name` | yes | contact person at that point |
| `phone_number_country_code` | yes | e.g. `60`, `65` |
| `phone_number` | yes | without the country code |
| `email` | no | |
| `remark` | no | free text passed to the rider — access notes, unit number, "call on arrival" |
| `packages` | yes | array, at least one item |

Each `packages` item:

| Field | Required | Notes |
|---|---|---|
| `quantity` | yes | |
| `height`, `width`, `depth` | yes | centimetres |
| `weight` | yes | **grams** — send `1200` for a 1.2 kg parcel, not `1.2` |
| `name` | no | what the item is |
| `description` | no | |
| `package_value` | no | declared value |

```json
{
  "api": "YOUR_API_KEY",
  "service_id": "EP-CS0K3M2P",
  "pickup_date": "2026-09-12",
  "pickup_time": "14:30:00",
  "waypoint": [
    {
      "type": "pickup",
      "latitude": 3.1421, "longitude": 101.6871,
      "address": "12 Jalan Example, 50450 Kuala Lumpur",
      "name": "Store Front", "email": "store@example.com",
      "phone_number_country_code": "60", "phone_number": "123456789",
      "remark": "Counter is on the ground floor",
      "packages": [
        { "name": "T-shirt", "quantity": 2, "height": 10, "width": 20, "depth": 15, "weight": 1200 }
      ]
    },
    {
      "type": "dropoff",
      "latitude": 3.1580, "longitude": 101.7120,
      "address": "88 Jalan Sample, 50200 Kuala Lumpur",
      "name": "Buyer Name", "email": "buyer@example.com",
      "phone_number_country_code": "60", "phone_number": "198765432",
      "remark": "Leave with the guard house",
      "packages": [
        { "name": "T-shirt", "quantity": 2, "height": 10, "width": 20, "depth": 15, "weight": 1200 }
      ]
    }
  ]
}
```

The parcels listed on a drop-off are what gets delivered there. For a single pickup and a single
drop-off, list the same parcels on both.

### Response

This action returns its fields at the **top level**, not under `result`:

```json
{
  "api_status": "Success",
  "error_code": "0",
  "error_remark": "",
  "order_number": "ED-4471",
  "price": "10.39",
  "tracking_url": "https://track.example/abc"
}
```

| Field | Notes |
|---|---|
| `order_number` | **Store this.** It is the handle for details and cancellation |
| `price` | What the account was charged, tax included |
| `tracking_url` | Courier's live tracking page. May be `null` until a driver is allocated |
| `addon_sms_notification_price` | Tracking sms charges |
| `addon_email_notification_price` | Tracking email charges |
| `addon_whatsapp_notification_price` | Tracking whatsapp charges |



A booking succeeded only when `order_number` is present **and** `error_code` is `0`. Persist
`order_number` before you do anything else — without it you cannot look the booking up or cancel it,
and the account has already been charged.

Placing an order is not idempotent. A timed-out request may still have booked; on a timeout, call
`OndemandOrderList` and look for a matching recent order before retrying.

---

## 5. `OndemandOrderDetails` — live status

The booking is live after placement: a driver gets allocated, then collects, then delivers. Poll
this action to follow it.

### Request

| Field | Required | Notes |
|---|---|---|
| `api` | yes | your API key |
| `order_id` | yes | the `order_number` from `OndemandPlaceOrder` |

### Response

```json
{
  "api_status": "Success",
  "error_code": "0",
  "result": {
    "id": "ED-4471",
    "status": 3,
    "status_text": "In Transit",
    "tracking_url": "https://track.example/abc",
    "pickup_time_from": "2026-09-12 14:30:00",
    "pickup_time_to": "2026-09-12 15:00:00",
    "created_at": "2026-09-12 14:05:00",
    "updated_at": "2026-09-12 14:41:00",
    "metadata": { "data": { "priceBreakdown": { "currency": "MYR" } } },
    "driver": {
      "name": "A Driver",
      "phone": "60123456789",
      "photo": "https://.../driver.jpg",
      "rating": "",
      "vehicle": { "physicalVehicleType": "Motorcycle", "model": "", "licensePlate": "WXY1234" }
    },
    "ondemand_service": {
      "service_info": {
        "support_type": "Document, Parcel",
        "payload": "20 kg",
        "dimension": "40 x 40 x 40 cm",
        "duration": "30 mins"
      },
      "ondemand_partner": {
        "full_name": "Lalamove Malaysia",
        "short_name": "Lalamove",
        "courier_image": "https://.../lalamove.png"
      },
      "ondemand_transportation": { "transportation": "Motorcycle" }
    },
    "ondemand_payments": { "paid_amount": "10.39" },
    "ondemand_order_waypoint": [
      {
        "type": 1,
        "name": "Store Front",
        "email": "store@example.com",
        "address": "12 Jalan Example, 50450 Kuala Lumpur",
        "phone_number_country_code": "60",
        "phone_number": "123456789",
        "coordinate": { "latitude": "3.1421", "longitude": "101.6871" },
        "note": "Counter is on the ground floor",
        "ondemand_packages": [
          {
            "name": "T-shirt",
            "quantity": 2,
            "dimensions": { "width": 20, "height": 10, "depth": 15, "weight": 1.2 }
          }
        ]
      }
    ]
  }
}
```

| Field | Notes |
|---|---|
| `id` | Same value you passed as `order_id` |
| `status` / `status_text` | See §8. Drive your UI off `status`; `status_text` is for display |
| `tracking_url` | Courier's live tracking page |
| `pickup_time_from` / `pickup_time_to` | The pickup window |
| `metadata.data.priceBreakdown.currency` | Currency of the amounts on this order |
| `driver` | `null` until a driver accepts. See below |
| `ondemand_service.service_info` | The vehicle's stated capability — what you saw at quote time |
| `ondemand_payments.paid_amount` | What the account was charged, tax included |
| `ondemand_order_waypoint` | The route, in visiting order. `type` is `1` for pickup, `2` for drop-off |
| `ondemand_order_waypoint[].coordinate` | `latitude` / `longitude` as strings |
| `ondemand_order_waypoint[].note` | The `remark` you sent for that point |

**`driver` only appears once a courier allocates one.** Before that it is `null`, or an object whose
`name`, `phone` and `photo` are all empty — check one of those three before rendering a driver card,
rather than checking that `driver` exists. `rating` and `vehicle.model` are frequently empty strings;
not every courier supplies them.

**Parcel dimensions use `depth`**, alongside `width` and `height` (all centimetres).

**`weight` comes back in kilograms here, but you send it in grams.** The unit is converted between
the two calls: submit `1200` for a 1.2 kg parcel, and read `1.2` back from this endpoint. This is
the one place in the API where a field changes unit between request and response — do not round-trip
a package straight from a details response into a new booking without multiplying by 1000.

**Linked courier accounts.** On an order booked against your own linked courier account,
`ondemand_payments` carries three extra fields: `byoc_charges` and `byoc_charges_tax` (the EasyParcel
platform fee charged to your EasyParcel credit — together they make up `paid_amount`) and
`shipment_price` (the delivery itself, billed by the courier to your own account). Their **presence**
is the marker; on an ordinary order they are absent. Do not test `byoc_charges` for truthiness — a
charge of `"0.00"` is a real value, meaning the order fell inside your free quota.

### Polling

Poll at a sane interval — every 20–30 seconds while the order is live is plenty. Stop polling once
`status` reaches a settled value (`0`, `4`, `5`, `6` or `7`); those never change again.

---

## 6. `OndemandOrderList` — recent orders

Lists the account's on-demand orders, newest first.

### Request

| Field | Required | Notes |
|---|---|---|
| `api` | yes | your API key |
| `limit` | no | page size. Default 10, maximum 250 |
| `last_order_id` | no | pagination cursor — see below |

### Response

```json
{
  "api_status": "Success",
  "error_code": "0",
  "total_orders": 137,
  "result": [ { "id": "ED-4471", "status": 6, "status_text": "Fulfilled", "…": "…" } ],
  "pagination": {
    "limit": 10,
    "has_more": true,
    "next_last_order_id": "ED-4462"
  }
}
```

Each row in `result` has the same shape as the `OndemandOrderDetails` payload **minus**
`ondemand_order_waypoint` — the route is details-only. Call `OndemandOrderDetails` when you need the
addresses, contacts or parcels.

### Paging

The cursor is keyset-based, not offset-based. Send the first page with no `last_order_id`; while
`pagination.has_more` is true, send `pagination.next_last_order_id` back as `last_order_id` for the
next page. `next_last_order_id` is `null` on the last page.

---

## 7. `OndemandCancelOrder` — cancel and refund

Cancels the booking at the courier and refunds the account in one step.

### Request

| Field | Required | Notes |
|---|---|---|
| `api` | yes | your API key |
| `order_id` | yes | the `order_number` from `OndemandPlaceOrder` |

### Response

```json
{
  "api_status": "Success",
  "error_code": "0",
  "result": "Order has been cancelled and refunded"
}
```

**`api_status` stays `Success` whether the cancellation worked or not.** `error_code` is what tells
you:

| `error_code` | Meaning |
|---|---|
| `0` | Cancelled at the courier and refunded |
| `-1` | Not cancelled. `error_remark` says why — surface it to the merchant |

A cancellation is refused once the courier is past the point of no return — typically when a driver
has already collected the parcel. There is no force-cancel: if the call fails, the delivery is still
live and the merchant should be told so, not shown a cancelled order.

Cancel the whole booking, not one drop-off. A multi-drop booking is one order and cancels as one.

---

## 8. Reference

### Order status

| `status` | `status_text` | Settled |
|---|---|---|
| `0` | Cancelled by Customer | yes |
| `1` | Pending | no — waiting for a courier to accept |
| `2` | Accepted | no — driver allocated |
| `3` | In Transit | no — parcel collected |
| `4` | Cancelled by Admin | yes |
| `5` | Cancelled by Driver | yes |
| `6` | Fulfilled | yes — delivered |
| `7` | Unable to Find Driver | yes |

Treat an unrecognised `status` as "in progress" and keep polling; `status_text` is `null` when we
have no label for a value, so never assume it is a non-empty string.

### Waypoint type

| Request (`OndemandQuotation`, `OndemandPlaceOrder`) | Response (`OndemandOrderDetails`) |
|---|---|
| `"pickup"` | `1` |
| `"dropoff"` | `2` |

The request takes strings and the response returns integers. This is a long-standing quirk of the
API; handle both.

### Identifiers

| Identifier | Where it comes from | Notes |
|---|---|---|
| `service_id` | `OndemandQuotation` | Identifies one courier service **for that quote**. Not stable across quotes — always book against a `service_id` from a fresh quote |
| `order_number` / `order_id` | `OndemandPlaceOrder` | Identifies the booking. Store it; it is the only handle for details and cancellation |

**Both are opaque strings.** Their prefixes differ between accounts and may change. Never strip a
prefix, pad a number, pattern-match on one, or reconstruct an id yourself — store the exact string
you were given and send back the exact string you stored.

### Amounts

JSON types are not consistent across actions: `paid_amount` is a decimal string (`"10.39"`), while
`estimate_price` on a quote may be a number **or** a string depending on the courier that produced
it. Parse every amount to a decimal type before using it, never compare amounts as strings, and do
not assume a fixed number of decimal places.

A courier that cannot price a route may return `"-"` in place of an amount. Treat a value that does
not parse as a number as "no price available" and hide that quote rather than rendering `NaN`.

---

## 9. Handling failures

| Symptom | What it means | What to do |
|---|---|---|
| `error_code` not `0` | The operation failed | Show `error_remark`. Do not retry blindly |
| `"Unauthorized user"` in `error_remark` | The API key is wrong, or wrong for this country's host | Check the key and that you are calling the matching base URL |
| Quote returns `result: []` | No courier serves that route or time | Ask the user to adjust the address or the pickup time |
| Place order times out | The booking may or may not have gone through | Call `OndemandOrderList` and look for a matching recent order before retrying |
| Cancel returns `error_code: -1` | Too late to cancel | Tell the merchant the delivery is still live. Never mark it cancelled locally |

Log `error_remark` verbatim when you hit something unexpected — it is the fastest thing for
EasyParcel support to work from.
