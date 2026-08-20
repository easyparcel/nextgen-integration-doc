# Preventing duplicate orders with `idempotency_key`

If your system retries a request after a network timeout, you can end up with two orders for
one shipment. A timeout means *you* stopped waiting — it does **not** mean the order failed.
The request usually finished on our side and created the order; you just never received the
response.

`idempotency_key` closes that gap. You attach a key to a submit request, and if you send the
same key again we return the **original response** instead of creating a second order.

---

## Quick start

Add one field to your request body:

```json
{
  "api": "your-api-key",
  "idempotency_key": "your-unique-reference",
  "bulk": [ ... ]
}
```

Then follow one rule: **when you retry, send the same key and the same body.**

That's it. No other change is required.

---

## Supported endpoints

| Method | Endpoint |
| ------ | -------- |
| POST | `EPSubmitOrderBulk` |
| POST | `MPSubmitOrderBulk` |

Paths are relative to the API base URL you already use.

**Payment endpoints do not accept this field, and do not need it.** Payment already
de-duplicates on the order numbers you send: if you call it twice for the same order, the
second call returns the existing order rather than charging again. This is also why you can
safely re-call payment to re-fetch an AWB that failed to generate the first time — you always
get the current state, never a cached copy.

---

## Choosing a key

- **One key per order attempt.** Generate it *before* your first send and store it with the
  order on your side, so a retry can reuse it.
- Your own order reference or a UUID both work well — `SHOP-ORDER-88421`,
  `9f1c2e04-6b7a-4e0e-9c11-2a5f7d3b8e10`.
- **Maximum 255 characters.** Longer values are truncated, which could make two different
  long keys collide. Keep them short.
- Surrounding whitespace is ignored.
- Keys only need to be unique **within your own integration** — you will never collide with
  another merchant. Keys are also tracked per endpoint, so the same key on a different
  endpoint is treated as a separate request.
- **Do not reuse a key for a genuinely new order.** A new shipment needs a new key.

---

## What happens when you send the same key again

| Situation | What you get |
| --------- | ------------ |
| First call | Processed normally. The response is stored. |
| Original **succeeded** | The **original response**, replayed exactly. No second order. |
| Original is **still running** | `error_code` **10**. Nothing is created. Retry with the same key. |
| Original returned an **error** | The key is released. Your retry is processed as a fresh request. |
| Same key, **different body** | `error_code` **11**. Nothing is created. |

### Errors release the key

If a submit fails — insufficient balance, an invalid postcode, a courier temporarily
unavailable — we do **not** store that response. The key becomes free again.

This is deliberate: it means you can fix the cause and retry with the **same** key. Top up
your wallet, correct the address, then re-send. You are not locked out for having failed once.


### Partial success is stored, not released

On a bulk submit, some parcels can succeed while others fail. That response has
`api_status: "Success"` with per-item errors inside `result`, and it **is** stored — because
the successful parcels really were created. Retrying that key replays the same mixed result;
it does not re-create the parcels that worked. Submit the failed parcels under a **new** key.

---

## How long a key is remembered

**24 hours**, measured from when the successful request completed.

After that the key is forgotten and sending it again is treated as a brand-new request — it
will create a new order. This is far longer than any retry needs, but do not rely on it as a
long-term duplicate check on your side.

---

## Retry guidance

1. **Generate and store the key before the first attempt.** A key you can't recover is a key
   you can't retry with.
2. **On a timeout, always retry with the same key.** Never assume the order failed.
3. **Wait longer than your own timeout before retrying.** A large bulk submit can take longer
   than a typical 30-second client timeout, and it keeps running after you disconnect. If you
   retry immediately you will just get `error_code 10`. Wait 30–60 seconds and back off
   between attempts.
4. **On `error_code 10`, keep the same key and try again shortly.** The original is still
   working. Each retry is safe and creates nothing.
5. **On `error_code 11`, your payload changed between attempts.** Send the original body, or
   use a new key if you really did intend a different order.
6. **Send a byte-identical body on retries.** Every field except `api` and `idempotency_key`
   is compared. `"weight": "1.000"` and `"weight": 1.0` count as different requests and will
   return `error_code 11`. Field *order* does not matter.

### Example flow

```
10:00:00  POST EPSubmiOrderBulk   key: SHOP-ORDER-88421
10:00:30  (your client times out — the request is still running on our side)
10:01:00  POST ... same key, same body   → error_code 10, "still being processed"
10:02:00  POST ... same key, same body   → 200, api_status Success, order EP-A1B2C3
10:05:00  POST ... same key, same body   → the same response again. Still one order.
```

---

## Error reference

Both are returned with HTTP `200` and `result: []`, in the standard response envelope.

### `error_code: "10"` — request in progress

```json
{
  "status_code": 200,
  "message": "",
  "data": {
    "result": [],
    "api_status": "Error",
    "error_code": "10",
    "error_remark": "A request with this idempotency key is still being processed. Retry with the same key to collect the result."
  }
}
```

Your earlier request with this key hasn't finished. **Nothing was created by this call.** Wait
and retry with the same key.

In the rare case of a failure on our side mid-request, a key held this way is released
automatically after 5 minutes, so you are never blocked indefinitely.

### `error_code: "11"` — key reused with a different request

```json
{
  "status_code": 200,
  "message": "",
  "data": {
    "result": [],
    "api_status": "Error",
    "error_code": "11",
    "error_remark": "This idempotency key was already used with a different request body."
  }
}
```

This key is already associated with a different payload. We return this instead of guessing,
because replaying the wrong order's response would be worse than refusing. Either send the
original body, or use a new key.

---

## Worked example

**First attempt**

```json
POST EPSubmitOrderBulk

{
  "idempotency_key": "SHOP-ORDER-88421",
  "api": "your-api-key",
  "bulk": [
    {
      "weight": "1.000",
      "content": "KUCING",
      "value": "225.00",
      "service_id": "EP-CS050",
      "cod_enabled": "1",
      "cod_amount": "225.00",
      "pick_name": "Ali",
      "pick_company": "Test Company",
      "pick_contact": "0123456789",
      "pick_addr1": "Lot 249",
      "pick_code": "11950",
      "pick_city": "Banting",
      "pick_state": "Selangor",
      "pick_country": "MY",
      "send_name": "Abu",
      "send_contact": "0123456789",
      "send_addr1": "Lot 248",
      "send_code": "11950",
      "send_city": "Banting",
      "send_state": "Selangor",
      "send_country": "MY",
      "collect_date": "2026-08-23"
    }
  ]
}
```

Your client times out at 30 seconds. You don't know whether the order exists.

**Retry — identical key, identical body**

You receive the response the first attempt produced, including the same order and parcel
numbers. One order exists, not two.

---

## Notes and limits

- **The field is optional.** Omit it and nothing changes — you get today's behaviour, with no
  duplicate protection. Protection applies only to requests that carry a key.
- **Marketplace requests:** the `authentication` field is part of the compared payload. If it
  changes between attempts you will get `error_code 11` rather than a replay, so keep it
  constant across retries of the same attempt.
