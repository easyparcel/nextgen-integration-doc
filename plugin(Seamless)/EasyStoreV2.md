# EasyParcel for EasyStore — Product Manual

**Version**: 1.0  
**Last updated**: 2026-06-23  

---

## Table of Contents

1. [Overview](#1-overview)
2. [Before You Begin — Get Your EasyParcel API Key](#2-before-you-begin--get-your-easyparcel-api-key)
3. [Install the App](#3-install-the-app)
4. [Settings Page](#4-settings-page)
   - 4.1 [Integration ID](#41-integration-id)
   - 4.2 [Sender Details](#42-sender-details)
   - 4.3 [Company Information & Pickup Location](#43-company-information--pickup-location)
   - 4.4 [Shipping Rates](#44-shipping-rates)
   - 4.5 [Handling Fees & Free Shipping](#45-handling-fees--free-shipping)
   - 4.6 [Fallback Shipping Rates](#46-fallback-shipping-rates)
5. [Fulfilling an Order](#5-fulfilling-an-order)
6. [Fulfilling Multiple Orders at Once (Bulk)](#6-fulfilling-multiple-orders-at-once-bulk)
7. [Printing Air Waybills (AWB)](#7-printing-air-waybills-awb)
   - 7.1 [Single Order AWB](#71-single-order-awb)
   - 7.2 [Bulk AWB Download](#72-bulk-awb-download)
8. [Tracking Parcel Status](#8-tracking-parcel-status)
9. [Uninstalling the App](#9-uninstalling-the-app)
10. [Troubleshooting](#10-troubleshooting)

---

## 1. Overview

**EasyParcel for EasyStore** is a logistics app that lives inside your EasyStore admin panel. It connects your EasyStore shop directly to EasyParcel Malaysia, so you can:

- Display **live shipping rates** from EasyParcel at your checkout
- **Fulfill orders** (book + pay for a parcel shipment) without leaving EasyStore admin
- **Print Air Waybills (AWB)** in A4 or 4"×6" sticker format
- Automatically **track parcels** and push status updates back to your EasyStore order timeline

Everything happens inside your EasyStore admin — no switching between apps.

---

## 2. Before You Begin — Get Your EasyParcel API Key

Before installing the app you need an **EasyParcel Integration ID** (API key). This key links the app to your EasyParcel account so it can fetch shipping rates and book parcels on your behalf.

If you already have an Integration ID, skip to [Section 3 — Install the App](#3-install-the-app).

Don't have an EasyParcel account yet? [Sign up here](https://p3x.cc/pv0t4R) first, then follow the steps below.

### Step 1 — Log in to EasyParcel

Go to [www.easyparcel.com](https://www.easyparcel.com) and log in to your account.

<img alt="Screenshot 2026-06-23 at 4 59 34 PM" src="https://github.com/user-attachments/assets/401898fc-8b62-4250-81ea-ecc9b5a44194" />


### Step 2 — Go to Integration and Add EasyStore

From the dashboard, navigate to **Integration** and select it. Then click **Add Ecommerce App**, find **EasyStore** in the list, and click **Install App**.

<img alt="Screenshot 2026-06-23 at 4 22 55 PM" src="https://github.com/user-attachments/assets/9553dedd-e37e-4ac2-8c6e-068af319a1bc" />


### Step 3 — Enter Your Store Details

Fill in your store's **name** and **web address (URL)**, then click **Add**.
<img alt="Screenshot 2026-06-23 at 4 42 28 PM" src="https://github.com/user-attachments/assets/a80b3241-3202-40a3-a2fc-c3428983f264" />


### Step 4 — Copy Your Integration ID

EasyParcel generates a unique **Integration ID (API key)** for your store. Copy this key — you will paste it into the EasyParcel for EasyStore app in the next section.

<img alt="image" src="https://github.com/user-attachments/assets/980d51fd-a5d5-42bd-986b-849be768f7a5" />


> **Keep this key safe.** It gives access to your EasyParcel account. Do not share it publicly.

---

## 3. Install the App

### Step 1 — Find the App

Click [here](https://www.easystore.co/en-my/apps/easyparcel-1) to go directly to the EasyParcel Malaysia app page on EasyStore, then click **Install this app**.
<img alt="image" src="https://github.com/user-attachments/assets/daa02cdb-dcd3-4d6d-a7cd-087c9d8b10c4" />


### Step 2 — Authorize the App

EasyStore will show a permission screen listing what the app needs access to (orders, fulfillments, shipping, locations). Click **Install** to authorize.

<img alt="image" src="https://github.com/user-attachments/assets/622f1f6d-4f4d-4580-8248-cd27bcc79ef1" />



### Step 3 — Complete Setup

After authorization you are taken to the **Settings page**. Complete all sections (Integration ID, sender details, pickup location) before the app is ready to use.

<img alt="Screenshot 2026-06-23 at 5 41 56 PM" src="https://github.com/user-attachments/assets/0895ec50-03fe-4b98-b63a-5fba9e800141" />


---

## 4. Settings Page

The Settings page is your control centre. Access it any time from your EasyStore admin → **Apps** → **EasyParcel Malaysia**.

---

### 4.1 Integration ID

Your **EasyParcel Integration ID** is the API key that allows this app to communicate with your EasyParcel account. Without it, no shipping rates will appear at checkout and you cannot fulfill orders.

**How to find your Integration ID:**

Follow the steps in [Section 2 — Before You Begin](#2-before-you-begin--get-your-easyparcel-api-key) to generate your Integration ID from EasyParcel's Integration dashboard.

**To enter it in the app:**

1. Paste your Integration ID into the **Integration ID** field
2. Click **Save** at the bottom of the page
3. The app will verify the ID against EasyParcel and display your current **credit balance** (e.g. "Balance: RM 25.00")

**Error: "Invalid integration ID. Please double check."**  
Your Integration ID did not pass verification. Check that you copied it completely and that your EasyParcel account is active.

---

### 4.2 Sender Details

This information appears on your Air Waybills as the sender/return address.

| Field | Description | Required |
|---|---|---|
| First Name | Your name or company contact's first name | Yes |
| Last Name | Last name | Yes |
| Mobile Number | Malaysian format: 01X-XXXXXXXX | Yes |
| Company Name | Optional — appears on the AWB | No |


---

### 4.3 Company Information & Pickup Location

This section links your **EasyStore Location** as the parcel pickup address. EasyParcel will collect parcels from this address.

**To set your pickup location:**

1. Make sure you have added your pickup address in EasyStore admin → **Settings** → **Locations** first
2. In the app Settings, open the **Company Information** section
3. Select your location from the **Location** dropdown
4. The address fields (Address, City, Postcode, State, Country) will auto-populate from EasyStore

> **Important:** If no location is selected, your customers will not see shipping rates at checkout and the fulfillment page will show a configuration error.

---

### 4.4 Shipping Rates

This section controls which shipping rate options appear at your store's checkout.

#### Enable EasyParcel Rate

The master toggle that turns EasyParcel shipping rates on or off.

| State | What customers see at checkout |
|---|---|
| **ON** | Live rates from EasyParcel (Pos Laju, J&T, DHL, etc.) |
| **OFF** | No EasyParcel rates — checkout shows "No shipping options" (or other shipping methods you have set up) |


#### With Dropoff (sub-option)

Only visible when **Enable EasyParcel Rate** is ON.

- **ON** — Dropoff services (where your customer drops the parcel at a collection point) are included in the rate list
- **OFF** — Only standard courier-pickup services are shown

#### Default Local Pickup Courier

When EasyParcel rates are enabled, select your preferred courier from the dropdown (25 Malaysian couriers available). This sets the default pre-selected courier on the fulfillment page.

#### Enable International Shipping Rate

Turn this on if you ship outside Malaysia. When enabled, EasyParcel will show international shipping rates to customers with non-Malaysian delivery addresses.

---

### 4.5 Handling Fees & Free Shipping

You can add a handling fee on top of EasyParcel's rates and/or offer free shipping above a certain order value. These settings are applied separately for **General** items and **Fragile** items.

#### Shipping Condition — General

Applied to all standard (non-fragile) products.

| Field | Description | Example |
|---|---|---|
| Handling Fee (MYR) | Fixed fee added to every rate | RM 2.00 |
| Handling Fee % | Percentage markup on top of the rate + fixed fee | 10% |
| Free Shipping Above (MYR) | Order subtotal threshold for free shipping | RM 150.00 |

**Calculation example:**

> EasyParcel rate: RM 8.50  
> + Handling Fee RM 2.00 → RM 10.50  
> + 10% → RM 11.55  
> Customer sees: **RM 11.55**

If the cart subtotal is RM 150.00 or above (and your free-shipping threshold is RM 150.00):  
> Customer sees: **RM 0.00**

#### Shipping Condition — Fragile

Same three fields, applied when any product in the cart is tagged as **Fragile** in EasyStore. Expand this section by clicking the **Fragile** heading.


---

### 4.6 Fallback Shipping Rates

A fallback rate is shown to customers when EasyParcel's API is temporarily unavailable or returns no results. This prevents your checkout from showing "No shipping options available."

#### Local Fallback

Shown for domestic (Malaysian) orders when EasyParcel returns no rates.

| Field | Description |
|---|---|
| Enable Local Fallback toggle | Turn on/off |
| Fallback Fee (MYR) | The flat rate shown to the customer |
| Fallback Name | Displayed as the shipping option name (e.g. "Standard Delivery") |
| Short Description | Subtitle shown under the name (e.g. "3–5 business days") |


#### International Fallback

Same fields, applied when the customer's delivery address is outside Malaysia.

---

### Saving Your Settings

Click the **Save** button at the bottom of the page. The app will:

1. Validate all required fields
2. Verify your Integration ID with EasyParcel
3. Save all settings and show a green "Settings saved." confirmation


---

## 5. Fulfilling an Order

When an order is ready to ship, you fulfill it directly from EasyStore without leaving your admin panel.

### Step 1: Open the Fulfillment Page

1. Go to EasyStore admin → **Orders**
2. Open the order you want to fulfill
3. Click **Fulfill** → select **Fulfill with EasyParcel**
<img  alt="image" src="https://github.com/user-attachments/assets/d819a2cc-ff3b-475b-b14b-8491c3826eb7" />


EasyStore opens the EasyParcel fulfillment page inside your admin.

<img width="1469" height="726" alt="Screenshot 2026-06-23 at 5 50 09 PM" src="https://github.com/user-attachments/assets/9af71455-c7fb-4c2c-9a32-7329b7b056ec" />


### Step 2: Review the Order Summary

The top of the page shows a read-only summary pulled from EasyStore:

- Order number (e.g. #1001)
- Customer name and delivery address
- Number of items and total weight


### Step 3: Set Parcel Details

| Field | Description |
|---|---|
| Pickup Date | Date you want EasyParcel to collect the parcel. Defaults to the next business day. |
| Delivery Option | **Pickup** (EasyParcel collects from you) or **Drop off** (you deliver to a collection point) |
| Drop-off Point | Only shown when "Drop off" is selected. Choose a nearby collection point. |
| Custom Weight | Toggle on to override the weight with your actual measured weight (kg). Minimum 0.1 kg. |
| Dimensions | Length × Width × Height in cm. Pre-filled from product data if available. |
| Declared Value | The declared value of the parcel (MYR). Defaults to the order subtotal. |
| Parcel Category | Select the category that best describes your product (e.g. Documents, Electronics, Apparel). |
| HS Code | Shown for international orders only. Required for customs clearance. |
| SMS Notification | Toggle on to send the recipient an SMS when EasyParcel picks up the parcel. |

<img alt="Screenshot 2026-06-23 at 5 50 09 PM" src="https://github.com/user-attachments/assets/a62609ae-9271-40f6-ad5b-dbdd955582fd" />
<img alt="Screenshot 2026-06-23 at 5 52 37 PM" src="https://github.com/user-attachments/assets/7f9716e7-120d-40cc-bce8-f46cd88215b5" />


### Step 4: Get a Rate Quote

Click **[Courier Service Section]**. The app queries EasyParcel and displays available courier options with prices and estimated delivery times.
<img alt="image" src="https://github.com/user-attachments/assets/b893f5e9-60cc-4fb6-8b6b-2b8af376468e" />
<img alt="Screenshot 2026-06-24 at 9 50 33 AM" src="https://github.com/user-attachments/assets/a6e3350d-3d14-4850-a979-ef42c6b8310a" />

Each rate shows:
- Courier logo and name (e.g. Pos Laju)
- Service name (e.g. Pos Laju Prepaid)
- Estimated delivery time
- Price (MYR)

Select the rate you want by clicking the radio button next to it.

**Insufficient balance?**  
If your EasyParcel credit balance is too low, a banner will appear. You can top up your balance on the EasyParcel dashboard, then try again.

### Step 5: Confirm the Booking

Click **[Fulfill now]**. In a single step the app will:

1. Book the parcel with EasyParcel
2. Pay for the parcel using your EasyParcel balance
3. Update the order on EasyStore with the tracking number
<img alt="image" src="https://github.com/user-attachments/assets/be9fffb6-50d9-4123-812a-be79166ba7d9" />
<img alt="image" src="https://github.com/user-attachments/assets/13affe53-c32e-47a4-b2fc-a13e332c4aec" />


### Step 6: View the Result

After a successful fulfillment, the success screen shows:

- Tracking number
- Courier and service name
- Tracking URL (clickable link)
- **[Download Air Waybill]** button
<img alt="Screenshot 2026-06-24 at 9 59 29 AM" src="https://github.com/user-attachments/assets/5ffd111f-f6e9-43a6-889b-17ed19af3d4e" />
<img alt="Screenshot 2026-06-24 at 10 03 25 AM" src="https://github.com/user-attachments/assets/c0229591-a3d0-4afc-86a7-db18324e6834" />



The EasyStore order timeline is automatically updated with the tracking number and courier details.

---

## 6. Fulfilling Multiple Orders at Once (Bulk)

If you have several orders to ship on the same day, bulk fulfillment lets you book and pay for all of them in one go — no need to open each order individually.

### Step 1 — Select Orders in EasyStore

1. Go to EasyStore admin → **Orders**
2. Tick the checkboxes next to the orders you want to fulfill
3. Click **Send Parcel** (or **Fulfill**) → select **EasyParcel Malaysia**

EasyStore opens the bulk fulfillment page inside your admin showing all selected orders.

> **[SCREENSHOT PLACEHOLDER: EasyStore orders list — multiple orders ticked, Send Parcel button highlighted]**

### Step 2 — Review Selected Orders

The page header shows the total number of orders being fulfilled and lists all order numbers (e.g. #1001, #1002, #1003).

> **[SCREENSHOT PLACEHOLDER: Bulk fulfillment page — order count header with order numbers listed]**

### Step 3 — Set Shared Parcel Details

The settings below apply to **all orders** in the batch:

| Field | Description |
|---|---|
| Pickup Date | Date EasyParcel collects all parcels |
| Delivery Option | **Pickup** or **Drop off** — applied to all orders |
| Drop-off Point | Shown when Drop off is selected; same point for all orders |
| Custom Weight | Toggle on to set a single weight (kg) applied to all orders |
| Parcel Dimensions | L × W × H (cm) — applied to all orders |
| Parcel Category | Category applied to all orders |
| SMS Notification | Toggle on to notify all recipients by SMS |

> **[SCREENSHOT PLACEHOLDER: Bulk fulfillment page — parcel details section]**

> **Note:** Declared value is taken automatically from each individual order's subtotal — it is not a shared field.

### Step 4 — Get a Rate Quote

Click **[Quote Shipping Rate]**. The app fetches rates from EasyParcel and shows a shared rate list. Select the courier and service you want — it will be applied to every order in the batch.

> **[SCREENSHOT PLACEHOLDER: Bulk fulfillment page — rate list with one option selected]**

### Step 5 — Fulfill All Orders

Click **[Fulfill All X Orders]**. The app processes the batch in the background and shows a live progress screen:

```
Fulfilling orders: 2 / 3 completed
  ✅ #1001 — Booked successfully
  ✅ #1002 — Booked successfully
  ⏳ #1003 — Processing...
```

> **[SCREENSHOT PLACEHOLDER: Bulk fulfillment progress screen — partially complete]**

Each order is booked, paid, and pushed to EasyStore automatically. If an individual order fails (e.g. insufficient balance mid-batch), it is marked as failed and the remaining orders continue processing.

### Step 6 — Download All AWBs

Once the batch is complete, click **[Download All AWBs]** to get a single merged PDF containing labels for all successfully fulfilled orders.

> **[SCREENSHOT PLACEHOLDER: Bulk fulfillment — completion screen with Download All AWBs button]**

---

## 7. Printing Air Waybills (AWB)

The Air Waybill (AWB) is the shipping label you attach to your parcel before handing it to the courier.

---

### 7.1 Single Order AWB

#### From the Fulfillment Success Screen

Click **[Download Air Waybill]** immediately after fulfillment. The AWB opens in a new browser tab as a PDF.

#### From an Existing Order (Reprint)

1. Go to EasyStore admin → **Orders** → open the fulfilled order
2. Click **Print AWB** → select **EasyParcel Malaysia**

The AWB page opens inside EasyStore admin.

> **[SCREENSHOT PLACEHOLDER: EasyStore order page — Print AWB button]**

#### Choosing a Format

At the top of the AWB page, select your preferred format:

| Format | Best for |
|---|---|
| **A4** (default) | Standard laser or inkjet printers |
| **Sticker 4"×6"** | Thermal label printers (Zebra, Brother, HPRT, etc.) |

Click the format you need, then click **[Download Air Waybill]**. The PDF opens in a new tab.

> **[SCREENSHOT PLACEHOLDER: AWB page — format selector with A4 selected]**

> **[SCREENSHOT PLACEHOLDER: AWB page — format selector with Sticker 4"×6" selected]**

> **Note:** You can reprint the AWB at any time — there is no limit on reprints.

---

### 7.2 Bulk AWB Download

After bulk fulfillment you can download all AWBs as a single merged PDF — one print job covers all your labels.

#### From the Bulk Fulfillment Completion Screen

Click **[Download All AWBs]** on the bulk fulfillment completion screen. See [Section 6 — Step 6](#step-6--download-all-awbs) for details.

#### From Existing Orders (Reprint)

1. Go to EasyStore admin → **Orders**
2. Tick the checkboxes next to the fulfilled orders
3. Click **Print AWB** → select **EasyParcel Malaysia**

The bulk AWB page opens and validates that all selected orders were fulfilled via EasyParcel.

> **[SCREENSHOT PLACEHOLDER: Bulk AWB page — order list with format selector]**

#### Format and Download

Select **A4** or **Sticker 4"×6"**, then click **[Download All AWBs (PDF)]**. A single merged PDF containing all labels downloads to your browser.

> **[SCREENSHOT PLACEHOLDER: Bulk AWB page — Download All AWBs button]**

> **Note:** If some selected orders were not fulfilled via EasyParcel, the page will warn you and offer to download only the ones that are available.

---

## 8. Tracking Parcel Status

Once an order is fulfilled, the app automatically monitors the parcel and keeps your EasyStore order timeline up to date — no manual action required.

### How It Works

The app checks the parcel status with EasyParcel every **30 minutes**. When the status changes, the order timeline in EasyStore is updated automatically.

### Parcel Status Stages

| Status | Meaning |
|---|---|
| Pending | Parcel booked, waiting for EasyParcel pickup |
| In Transit | EasyParcel has collected the parcel and it is moving |
| Out for Delivery | Parcel is on the delivery vehicle |
| Delivered | Parcel delivered to the recipient |
| Failed | Delivery attempt failed |
| Returned | Parcel returned to sender |

### Customer Notifications

When the parcel status reaches **Delivered**, EasyStore automatically sends a notification email to your customer. This is handled by EasyStore — you do not need to do anything.

### Viewing Tracking on an Order

1. EasyStore admin → **Orders** → open the fulfilled order
2. The order timeline shows the current status and tracking number
3. Click the tracking URL to view the full EasyParcel tracking page

> **[SCREENSHOT PLACEHOLDER: EasyStore order timeline — tracking status entries]**

---

## 9. Uninstalling the App

To remove the app from your store:

1. EasyStore admin → **Apps** → **EasyParcel Malaysia** → **Uninstall**

Your settings, fulfillment history, and tracking logs are **retained**. If you reinstall the app in the future, you only need to re-authorize with EasyStore — all your previous settings will still be there.

---

## 10. Troubleshooting

### No shipping rates appear at checkout

Check the following in Settings:

1. **Integration ID** is entered and validated (balance badge should be visible)
2. **Enable EasyParcel Rate** toggle is ON
3. A **Pickup Location** is selected under Company Information
4. Your origin address (pickup location) is a valid Malaysian address with a correct postcode

If all of the above are correct, check if you have a **Fallback Rate** configured so customers always see at least one shipping option.

---

### "Invalid integration ID. Please double check."

Your Integration ID failed verification. Confirm that:
- You copied the ID without extra spaces
- Your EasyParcel account is active and not suspended
- You are using the Integration ID (API key), not your EasyParcel login password

---

### Fulfillment fails with "Insufficient balance"

Your EasyParcel wallet does not have enough credit to pay for the shipment. Top up your balance at [EasyParcel Dashboard](https://www.easyparcel.com), then try fulfilling the order again.

---

### AWB download shows "AWB is only available for orders fulfilled via EasyParcel"

This order was not fulfilled using this app (it may have been fulfilled manually or via another app). AWB download is only available for orders booked through EasyParcel for EasyStore.

---

### Checkout shows rates but they seem too high

Check your handling fee and percentage settings in the Settings page:
- **Handling Fee** — a flat fee added to every rate
- **Handling Fee %** — a percentage markup on top

Reduce or clear these fields if you don't want any markup.

---

### Tracking status hasn't updated in a long time

The tracking poll runs every 30 minutes. If the status has not changed for more than an hour:
1. Check the EasyParcel tracking page directly (the tracking URL is on the order timeline)
2. If EP tracking shows a new status, it will sync automatically on the next poll cycle

---

*For further help, visit the [EasyStore Help Centre](https://support.easystore.co) or contact EasyParcel support.*

