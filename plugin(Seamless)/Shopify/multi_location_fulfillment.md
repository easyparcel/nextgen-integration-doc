# Fulfill from Multiple Locations — Shopify

If your Shopify store keeps stock in more than one place — for example a warehouse in Malaysia and another in Singapore — the EasyParcel app can ship each order from where its items actually are. When an order's items sit at different Shopify locations, the order page splits it into **one shipment per location**, each with its own pickup address, courier and price. You can check everything in one summary, then fulfill the locations one at a time or all at once.

> ℹ️ This works when you fulfill an order from its **order page** with **Standard** delivery. Bulk fulfillment, On-Demand delivery and auto-fulfillment are not affected (auto-fulfillment has its own location setting).

---

## Table of contents

1. [Before you start](#1-before-you-start)
2. [Turn on shipping from your Shopify locations](#2-turn-on-shipping-from-your-shopify-locations)
3. [How an order is split](#3-how-an-order-is-split)
4. [Check the booking summary](#4-check-the-booking-summary)
5. [Review and edit each location's shipment](#5-review-and-edit-each-locations-shipment)
6. [Fulfill one location](#6-fulfill-one-location)
7. [Fulfill all locations at once](#7-fulfill-all-locations-at-once)
8. [Ship the whole order as one shipment](#8-ship-the-whole-order-as-one-shipment)
---

## 1. Before you start

You'll need:

- The **EasyParcel** app installed and connected to a **verified** EasyParcel account.
- Your locations set up in Shopify (**Shopify admin → Settings → Locations**), each with a **full address** (street, city, postcode) and a **phone number**. This is where the courier will collect from.
- Your stock recorded at the right locations. Shopify decides which location each item of an order ships from, based on where the stock is and your order routing settings (**Shopify admin → Settings → Shipping and delivery**).
- A **default sender address** in the app (**Setting → Sender Details**). Its contact name is used on every shipment.
- Enough **EasyParcel credit**. Each location is booked as a separate shipment and charged separately.

---

## 2. Turn on shipping from your Shopify locations

1. In the EasyParcel app, go to **Setting**.
2. In the **Sender Details** section, find **Ship orders from (single order fulfillment)**.
3. Choose **The Shopify location the items are assigned to**.

The setting saves straight away and you'll see *"Single order fulfillments will ship from the Shopify location their items are assigned to"*.
<img alt="image" src="https://github.com/user-attachments/assets/cc0776b2-1035-4a08-bcb2-b1fb4257d750" />


With this setting on, each shipment uses:

| Detail | Comes from |
|---|---|
| Pickup address | The Shopify location's address |
| Phone number | The Shopify location's phone (your default sender's phone if the location has none) |
| Contact name | Your default sender address |

If you change a location's address or phone in Shopify, the new details are used the next time you open the order.

> 💡 You can still change the pickup address of any shipment on the order page

To go back to the original behaviour, choose **My default sender address**. Orders then ship as one shipment from your default sender address, as before.

---

## 3. How an order is split

Go to **Orders** and open an unfulfilled order.

- **All items at one location** — you get one shipment, picked up from that location.
- **Items at two or more locations** — the order is split into one shipment per location. The heading shows how many, e.g. **Unfulfilled (3) · 2 locations**, with **Ship as one shipment** and **Fulfill all locations** buttons next to it.
- **One item split between locations** — if Shopify takes, say, 2 units from Malaysia and 1 from Singapore, the item appears in both shipments with each location's share.
  <img alt="image" src="https://github.com/user-attachments/assets/24a76d54-b433-474c-a898-203094ea7ea1" />


---

## 4. Check the booking summary

At the top of the order page, the **Booking summary** lists every shipment on one line so you don't have to scroll through each one:

- the **location** name
- its **status**
- the **courier** (logo and service)
- the **price**
- an **edit** button, which takes you to that shipment
- a **Fulfill** button, to book that location right from the summary

A **Total** line at the bottom adds up all the locations.
<img alt="image" src="https://github.com/user-attachments/assets/ac62fb82-5d44-4fb9-80b3-5fec93ba0e7f" />


**What the status means:**

| Status | Meaning |
|---|---|
| **Getting rates…** | Prices are being fetched, for example after you changed an address, weight or courier. |
| **Ready** | The shipment can be booked. |
| **Booking…** | The shipment is being booked. |
| **Booked** | Done. It will move to your fulfilled shipments. |
| An orange reason, e.g. **No courier rates**, **Check the weight and size**, **Edit the parcel content** | Something on that shipment needs fixing first. |

**See the details:** click anywhere on a row to open it. You'll see the items (with quantity and SKU), the full pickup address, the pickup date or drop-off point, parcel weight and size, declared value, content, category and HS code. Add-ons are shown as coloured labels: **EasyCover**, **DDP** and **Coupon**.

**Edit a detail:** click the edit icon right after any detail. The app opens that location's shipment, scrolls to the field and highlights it.

> ℹ️ Orders that ship as a single shipment also get a booking summary, with its one row already open.

---

## 5. Review and edit each location's shipment

Below the summary, **Fulfillment by location** has a **tab for each location**. Each tab shows that location's price, or **No rates** if no courier is available. Click a tab to see that location's shipment, titled **Ship from** and the location name.

<img alt="image" src="https://github.com/user-attachments/assets/a1e8832c-7bdc-44de-88ef-871b5fcc969d" />

You can change everything just like on a normal order — items and quantities, weight and size, parcel content, declared value, category, HS code, pickup address, courier, pickup date or drop-off point, EasyCover, DDP and coupons.

- Changes on one location **don't affect the others**, and they're **kept when you switch tabs**.
- Weight, size and declared value are worked out for **that location's items only**.
- To pick up from somewhere else, change the sender address. The location's own address is listed with an **Assigned location** label, so you can always switch back to it.
  <img alt="image" src="https://github.com/user-attachments/assets/794c90e9-c5dd-498d-a73f-b00967cd1987" />


> 💡 Shipments can be long. Use the **Back to summary** button at the bottom-right of the page to jump back up to the booking summary.

---

## 6. Fulfill one location

1. Make sure the location shows **Ready** in the booking summary.
2. Click **Fulfill this location** at the bottom of its tab, **or** **Fulfill** on its row in the booking summary.

The shipment is booked and paid, and that location's items are marked as fulfilled in Shopify with the tracking number, so your customer is notified.

The page updates **without reloading**: the booked location moves to your fulfilled shipments, and the other locations keep everything you've entered. Their prices are refreshed in case something changed, for example a coupon that has now been used.

<img alt="image" src="https://github.com/user-attachments/assets/95fb71df-8b5a-492f-ac41-52bf2f3c9ec3" />


---

## 7. Fulfill all locations at once

1. Wait until every location shows **Ready** in the booking summary.
2. Click **Fulfill all locations** at the top of the order.

The locations are booked one after another. A finished location shows **Booked** while the next one is booking. When all are done, you'll see your wallet balance as usual.

If a location can't be booked, the app carries on with the rest (except in the cases listed further down) and a message tells you what happened:

- **Fulfilled:** the locations that were booked.
- **Not fulfilled:** the location that wasn't, and why.
- **Not attempted:** locations that were left for you to book.

The location that needs your attention is brought to the front, so you can fix it and click **Fulfill this location**.
<img alt="image" src="https://github.com/user-attachments/assets/ec8634c2-64d5-4ccc-9730-8c734ab01c8b" />

---

## 8. Ship the whole order as one shipment

Sometimes you'd rather send everything in one parcel, for example when you've already moved the items to one place.

1. Click **Ship as one shipment** at the top of the order.
2. The order becomes a single shipment from your **default sender address**. A note tells you the items are assigned to several Shopify locations but ship here as one shipment.
3. Fulfill it as usual. In Shopify, the items are marked as fulfilled at each of their locations, all with the same tracking number.

To go back, click **Split by location** in that note.

<img alt="image" src="https://github.com/user-attachments/assets/86209847-3453-448b-a94d-b03cd427275a" />

> ℹ️ This choice is only for this visit. If you leave and reopen the order, it's split by location again.

