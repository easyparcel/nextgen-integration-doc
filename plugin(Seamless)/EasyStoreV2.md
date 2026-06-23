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
6. [Printing Air Waybills (AWB)](#6-printing-air-waybills-awb)
7. [Tracking Parcel Status](#7-tracking-parcel-status)
8. [Uninstalling the App](#8-uninstalling-the-app)
9. [Troubleshooting](#9-troubleshooting)

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

<img width="100" height="auto" alt="Screenshot 2026-06-23 at 4 59 34 PM" src="https://github.com/user-attachments/assets/401898fc-8b62-4250-81ea-ecc9b5a44194" />


### Step 2 — Go to Integration and Add EasyStore

From the dashboard, navigate to **Integration** and select it. Then click **Add Ecommerce App**, find **EasyStore** in the list, and click **Install App**.

<img alt="Screenshot 2026-06-23 at 4 22 55 PM" src="https://github.com/user-attachments/assets/9553dedd-e37e-4ac2-8c6e-068af319a1bc" />


### Step 3 — Enter Your Store Details

Fill in your store's **name** and **web address (URL)**, then click **Add**.
<img alt="Screenshot 2026-06-23 at 4 42 28 PM" src="https://github.com/user-attachments/assets/a80b3241-3202-40a3-a2fc-c3428983f264" />


### Step 4 — Copy Your Integration ID

EasyParcel generates a unique **Integration ID (API key)** for your store. Copy this key — you will paste it into the EasyParcel for EasyStore app in the next section.

> **[SCREENSHOT PLACEHOLDER: Integration — Integration ID displayed with Copy button]**

> **Keep this key safe.** It gives access to your EasyParcel account. Do not share it publicly.

---

## 3. Install the App

### Step 1 — Find the App

Go to your EasyStore admin → **Apps** → search for **EasyParcel Malaysia** → click **Install**.

> **[SCREENSHOT PLACEHOLDER: App Store listing — EasyParcel Malaysia card]**

### Step 2 — Authorize the App

EasyStore will show a permission screen listing what the app needs access to (orders, fulfillments, shipping, locations). Click **Install App** to authorize.

> **[SCREENSHOT PLACEHOLDER: OAuth permission screen]**

The app needs the following permissions to work correctly:

| Permission | Why it's needed |
|---|---|
| Read & write orders | Fetch order details and mark orders as fulfilled |
| Read & write fulfillments | Create fulfillment records and update tracking status |
| Read locations | Auto-populate your pickup address |
| Read & write shipping | Register shipping rate webhooks |
| Read customers & products | Display order details on the fulfillment page |

### Step 3 — Complete Setup

After authorization you are taken to the **Settings page**. Complete all sections (Integration ID, sender details, pickup location) before the app is ready to use.

> **[SCREENSHOT PLACEHOLDER: Settings page after fresh install — empty state]**

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

> **[SCREENSHOT PLACEHOLDER: Integration ID field — valid key with balance badge]**

**Error: "Invalid integration ID. Please double check."**  
Your Integration ID did not pass verification. Check that you copied it completely and that your EasyParcel account is active.

> **[SCREENSHOT PLACEHOLDER: Integration ID field — inline error state]**

---

### 4.2 Sender Details

This information appears on your Air Waybills as the sender/return address.

| Field | Description | Required |
|---|---|---|
| First Name | Your name or company contact's first name | Yes |
| Last Name | Last name | Yes |
| Mobile Number | Malaysian format: 01X-XXXXXXXX | Yes |
| Company Name | Optional — appears on the AWB | No |

> **[SCREENSHOT PLACEHOLDER: Sender Details section filled in]**

---

### 4.3 Company Information & Pickup Location

This section links your **EasyStore Location** as the parcel pickup address. EasyParcel will collect parcels from this address.

**To set your pickup location:**

1. Make sure you have added your pickup address in EasyStore admin → **Settings** → **Locations** first
2. In the app Settings, open the **Company Information** section
3. Select your location from the **Location** dropdown
4. The address fields (Address, City, Postcode, State, Country) will auto-populate from EasyStore

> **[SCREENSHOT PLACEHOLDER: Company Information — location dropdown with address auto-filled]**

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

> **[SCREENSHOT PLACEHOLDER: Enable EasyParcel Rate toggle — ON state]**

#### With Dropoff (sub-option)

Only visible when **Enable EasyParcel Rate** is ON.

- **ON** — Dropoff services (where your customer drops the parcel at a collection point) are included in the rate list
- **OFF** — Only standard courier-pickup services are shown

#### Default Local Pickup Courier

When EasyParcel rates are enabled, select your preferred courier from the dropdown (25 Malaysian couriers available). This sets the default pre-selected courier on the fulfillment page.

#### Enable International Shipping Rate

Turn this on if you ship outside Malaysia. When enabled, EasyParcel will show international shipping rates to customers with non-Malaysian delivery addresses.

> **[SCREENSHOT PLACEHOLDER: International rate toggle — enabled]**

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

> **[SCREENSHOT PLACEHOLDER: Fragile section expanded with values entered]**

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

> **[SCREENSHOT PLACEHOLDER: Local Fallback section filled in]**

#### International Fallback

Same fields, applied when the customer's delivery address is outside Malaysia.

---

### Saving Your Settings

Click the **Save** button at the bottom of the page. The app will:

1. Validate all required fields
2. Verify your Integration ID with EasyParcel
3. Save all settings and show a green "Settings saved." confirmation

> **[SCREENSHOT PLACEHOLDER: Settings page with green success toast]**

---

## 5. Fulfilling an Order

When an order is ready to ship, you fulfill it directly from EasyStore without leaving your admin panel.

### Step 1: Open the Fulfillment Page

1. Go to EasyStore admin → **Orders**
2. Open the order you want to fulfill
3. Click **Fulfill** → select **EasyParcel Malaysia**

EasyStore opens the EasyParcel fulfillment page inside your admin.

> **[SCREENSHOT PLACEHOLDER: EasyStore order page — Fulfill button with EasyParcel option]**

### Step 2: Review the Order Summary

The top of the page shows a read-only summary pulled from EasyStore:

- Order number (e.g. #1001)
- Customer name and delivery address
- Number of items and total weight

> **[SCREENSHOT PLACEHOLDER: Fulfillment page — order summary header]**

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

> **[SCREENSHOT PLACEHOLDER: Fulfillment page — parcel details section filled in]**

### Step 4: Get a Rate Quote

Click **[Quote Shipping Rate]**. The app queries EasyParcel and displays available courier options with prices and estimated delivery times.

> **[SCREENSHOT PLACEHOLDER: Fulfillment page — rate list showing multiple couriers]**

Each rate shows:
- Courier logo and name (e.g. Pos Laju)
- Service name (e.g. Pos Laju Prepaid)
- Estimated delivery time
- Price (MYR)

Select the rate you want by clicking the radio button next to it.

**Insufficient balance?**  
If your EasyParcel credit balance is too low, a banner will appear. You can top up your balance on the EasyParcel dashboard, then try again.

### Step 5: Confirm the Booking

Click **[Fulfill Order]**. In a single step the app will:

1. Book the parcel with EasyParcel
2. Pay for the parcel using your EasyParcel balance
3. Update the order on EasyStore with the tracking number

> **[SCREENSHOT PLACEHOLDER: Fulfillment page — loading state after clicking Fulfill Order]**

### Step 6: View the Result

After a successful fulfillment, the success screen shows:

- Tracking number
- Courier and service name
- Tracking URL (clickable link)
- **[Download Air Waybill]** button

> **[SCREENSHOT PLACEHOLDER: Fulfillment page — success screen with tracking number]**

The EasyStore order timeline is automatically updated with the tracking number and courier details.

---

## 6. Printing Air Waybills (AWB)

The Air Waybill is the shipping label you attach to your parcel.

### From the Fulfillment Success Screen

Click **[Download Air Waybill]** immediately after fulfillment. The AWB opens in a new browser tab as a PDF.

### From an Existing Order (Reprint)

1. Go to EasyStore admin → **Orders** → open the fulfilled order
2. Click **Print AWB** → select **EasyParcel Malaysia**

The AWB page opens inside EasyStore admin.

> **[SCREENSHOT PLACEHOLDER: EasyStore order page — Print AWB button]**

### Choosing a Format

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

## 7. Tracking Parcel Status

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

## 8. Uninstalling the App

To remove the app from your store:

1. EasyStore admin → **Apps** → **EasyParcel Malaysia** → **Uninstall**

Your settings, fulfillment history, and tracking logs are **retained**. If you reinstall the app in the future, you only need to re-authorize with EasyStore — all your previous settings will still be there.

---

## 9. Troubleshooting

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
