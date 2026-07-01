# EasyParcel for EasyStore — Product Manual

**Version**: 1.1  
**Last updated**: 2026-07-01  

---

## Table of Contents

1. [Overview](#1-overview)
2. [Before You Begin — Get Your EasyParcel API Key](#2-before-you-begin--get-your-easyparcel-api-key)
3. [Install the App](#3-install-the-app)
4. [Settings Page](#4-settings-page)
   - 4.0 [Managing Your Regions](#40-managing-your-regions)
   - 4.1 [Integration ID](#41-integration-id)
   - 4.2 [Sender Details](#42-sender-details)
   - 4.3 [Company Information & Pickup Location](#43-company-information--pickup-location)
   - 4.4 [Shipping Rates](#44-shipping-rates)
   - 4.5 [Handling Fees & Free Shipping](#45-handling-fees--free-shipping)
   - 4.6 [Fallback Shipping Rates](#46-fallback-shipping-rates)
   - 4.7 [Default Parcel Content](#47-default-parcel-content)
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

**EasyParcel for EasyStore** is a logistics app that lives inside your EasyStore admin panel. It connects your EasyStore shop to EasyParcel, so you can:

- Display **live shipping rates** from EasyParcel at your checkout
- **Fulfill orders** (book + pay for a parcel shipment) without leaving EasyStore admin
- **Print Air Waybills (AWB)**
- Automatically **track parcels** and push status updates back to your EasyStore order timeline

Everything happens inside your EasyStore admin — no switching between apps.

> **Shipping from more than one region?** The app supports multiple **regions** in a single install. Each region has its own EasyParcel account, sender details, and pickup location — for example one for Malaysia and one for Singapore. If you only ship from one country you can ignore the multi-region features; the app works exactly the same with a single region. See [4.0 Managing Your Regions](#40-managing-your-regions).

---

## 2. Before You Begin — Get Your EasyParcel API Key

Before installing the app you need an **EasyParcel Integration ID** (API key). This key links the app to your EasyParcel account so it can fetch shipping rates and book parcels on your behalf.

> **One Integration ID per region.** If you ship from more than one country, you will generate a separate Integration ID for each EasyParcel account and add one region per account in the app (see [Section 4](#4-settings-page)).

If you already have an Integration ID, skip to [Section 3 — Install the App](#3-install-the-app).

Don't have an EasyParcel account yet? [Sign up here](https://p3x.cc/pv0t4R) first, then follow the steps below.

### Step 1 — Log in to EasyParcel

Go to [www.easyparcel.com](https://www.easyparcel.com) and log in to your account.

<img alt="Screenshot 2026-06-23 at 4 59 34 PM" src="https://github.com/user-attachments/assets/401898fc-8b62-4250-81ea-ecc9b5a44194" />


### Step 2 — Go to Integration and Add EasyStore

From the dashboard, navigate to **Integration** and select it. Then click **Add Ecommerce App**, find **EasyStore** in the list, and click **Install App**.

<img alt="Screenshot 2026-06-23 at 4 22 55 PM" src="https://github.com/user-attachments/assets/9553dedd-e37e-4ac2-8c6e-068af319a1bc" />


### Step 3 — Enter Your Store Details

Fill in your store's **name** and **web address (URL)**, then click **Add**.
<img alt="Screenshot 2026-07-01 at 3 31 08 PM" src="https://github.com/user-attachments/assets/7dbbdfaa-1b0d-4858-bec3-c243bca66d74" />



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

After authorization, EasyStore opens the EasyParcel app on its **Settings page**. Complete all sections — Integration ID, sender details, and pickup location — for each region you ship from before the app is ready to use.

<img alt="Screenshot 2026-06-23 at 5 41 56 PM" src="https://github.com/user-attachments/assets/0895ec50-03fe-4b98-b63a-5fba9e800141" />


---

## 4. Settings Page

The Settings page is your control centre. Access it any time from your EasyStore admin → **Apps** → **EasyParcel Malaysia**.

---

### 4.0 Managing Your Regions

Your settings are organised into **regions**. Each region is a separate EasyParcel account with its own Integration ID, sender details, pickup location, rate options, and fees — for example a Malaysia region and a Singapore region. If you ship from a single country you'll simply have one region, and everything below still applies.

Regions appear as **cards** at the top of the Settings page:

- **Select a region** — click its card to open it for editing. The active card is highlighted and shows an **Editing** badge.
- **Add a region** — click **Add region**, then fill in the Integration ID, sender details, and pickup location for the new EasyParcel account and Save.
- **Set as default** — the default region is used when the app can't automatically match an order to a specific region. Open a region and click **Set default**.
- **Delete a region** — open the region and click delete (you'll be asked to confirm). Existing shipments already booked under that region are not affected. You cannot delete your only remaining region.

> **How the app picks a region for an order:** at checkout the app matches the customer's destination/origin to the right region automatically; when you fulfill, it matches the order's pickup location, then falls back to your default region. You can always override this with the **Ship from** selector on the fulfillment page (see [Section 5](#5-fulfilling-an-order)).

---

### 4.1 Integration ID

Your **EasyParcel Integration ID** is the API key that allows this app to communicate with your EasyParcel account. Without it, no shipping rates will appear at checkout and you cannot fulfill orders. Each region has its own Integration ID.

**How to find your Integration ID:**

Follow the steps in [Section 2 — Before You Begin](#2-before-you-begin--get-your-easyparcel-api-key) to generate your Integration ID from EasyParcel's Integration dashboard.

**To enter it in the app:**

1. Select (or add) the region you want to configure
2. **Choose your pickup location first** (see [4.3](#43-company-information--pickup-location)) — the app needs to know the region so it can verify the ID against the correct EasyParcel service
3. Paste your Integration ID into the **Integration ID** field
4. Click **Save** — the app verifies the ID against EasyParcel as part of saving
5. On success it displays your current **credit balance** (e.g. "Credit balance: MYR 25.00") and the **EasyParcel API version** badge

**Error: "Invalid integration ID. Please double check."**  
Your Integration ID did not pass verification. Check that you copied it completely and that your EasyParcel account is active.

> If EasyParcel can't be reached at the moment you Save, the app still saves your other settings and shows: "Settings saved — but could not verify Integration ID against EasyParcel right now." Re-check the balance badge later.

---

### 4.2 Sender Details

This information appears on your Air Waybills as the sender/return address. Sender details are set per region.

| Field | Description | Required |
|---|---|---|
| First Name | Your name or company contact's first name | Yes |
| Last Name | Last name | No |
| Mobile Phone | Malaysian format: 01X-XXXXXXXX | Yes |
| Email | Sender/return email | No |
| Company Name | Optional — appears on the AWB | No |

> **Tip:** When you select a pickup location, the app pre-fills the Mobile Phone and Email from that location if you've left them blank. You can override them.

---

### 4.3 Company Information & Pickup Location

This section links your **EasyStore Location** as the parcel pickup address. EasyParcel will collect parcels from this address. The pickup location is set per region.

**To set your pickup location:**

1. Make sure you have added your pickup address in EasyStore admin → **Settings** → **Locations** first
2. In the app Settings, open the **Company Information** section
3. Select your location from the **Location** dropdown (use **Reload** if you just added a location in EasyStore and don't see it yet)
4. The address fields (Address, City, Postcode/Zip, State/Province, Country) auto-populate from EasyStore and are read-only

> **Important:** If no location is selected, your customers will not see shipping rates at checkout and the fulfillment page will show a configuration error. If the dropdown is empty, add a location in EasyStore admin → **Settings** → **Locations** and click **Reload**.

---

### 4.4 Shipping Rates

This section controls which shipping rate options appear at your store's checkout.

#### Enable EasyParcel Rate

The master toggle that turns EasyParcel shipping rates on or off.

| State | What customers see at checkout |
|---|---|
| **ON** | Live rates from EasyParcel (Pos Laju, J&T, DHL, etc.) |
| **OFF** | No EasyParcel rates — checkout shows "No shipping options" (or other shipping methods you have set up) |


#### Enable EasyParcel Rate with Dropoff (sub-option)

Only visible when **Enable EasyParcel Rate** is ON.

- **ON** — Dropoff services (where your customer drops the parcel at a collection point) are included in the rate list
- **OFF** — Only standard courier-pickup services are shown

#### Default Local Pickup Courier

When EasyParcel rates are enabled, select your preferred courier from the dropdown. The list is populated with the couriers available for the region's country. This sets the default pre-selected courier on the fulfillment page.

#### Exclude Couriers from Checkout Rates

Tick any couriers you don't want shown to customers at checkout. Excluded couriers are hidden from the rate list for that region.

#### Enable EasyParcel International Rate

Turn this on if you ship outside the region's home country. When enabled, EasyParcel will show international shipping rates to customers with delivery addresses in other countries.

---

### 4.5 Handling Fees & Free Shipping

You can add a handling fee on top of EasyParcel's rates and/or offer free shipping above a certain order value. These settings are applied separately for **General** items and **Fragile** items, and are set per region.

#### Shipping Condition — General

Applied to all standard (non-fragile) products.

| Field | Description | Example |
|---|---|---|
| Handling Fee | Fixed fee added to every rate | RM 2.00 |
| Percentage | Percentage adjustment on top of the rate + fixed fee. Positive marks up; a negative value discounts. | 10% |
| Free Shipping Above | Order subtotal threshold for free shipping (0 = disabled) | RM 150.00 |

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

A fallback rate is shown to customers when EasyParcel's API is temporarily unavailable or returns no results. This prevents your checkout from showing "No shipping options available." Fallback rates are set per region.

#### Local Fallback

Shown for domestic orders when EasyParcel returns no rates.

| Field | Description |
|---|---|
| Enable Local Fallback toggle | Turn on/off |
| Fee | The flat rate shown to the customer |
| Shipping Name | Displayed as the shipping option name (e.g. "Standard Delivery") |
| Short Description | Subtitle shown under the name (e.g. "3–5 business days") |


#### International Fallback

Same fields, applied when the customer's delivery address is outside the region's home country.

---

### 4.7 Default Parcel Content

Sets what the app puts in the parcel **content** field when booking with EasyParcel. This is per region and can be overridden per shipment on the fulfillment page.

- **SKU** (default) — uses each item's SKU, and falls back to the product name for any item that has no SKU
- **Product name** — always uses the product name

---

### Saving Your Settings

Click the **Save** button at the bottom of the page. The app will:

1. Validate all required fields (region label, Integration ID, sender first name, sender mobile phone, pickup location)
2. Verify your Integration ID with EasyParcel (non-blocking — your settings still save if EasyParcel is briefly unreachable)
3. Save all settings and show a green **"Successfully Updated"** confirmation


---

## 5. Fulfilling an Order

When an order is ready to ship, you fulfill it directly from EasyStore without leaving your admin panel.

### Step 1: Open the Fulfillment Page

1. Go to EasyStore admin → **Orders**
2. Open the order you want to fulfill
3. Click **Fulfill** → select **Fulfill with EasyParcel**
<img  alt="image" src="https://github.com/user-attachments/assets/d819a2cc-ff3b-475b-b14b-8491c3826eb7" />


EasyStore opens the EasyParcel fulfillment page inside your admin.

<img alt="Screenshot 2026-06-23 at 5 50 09 PM" src="https://github.com/user-attachments/assets/9af71455-c7fb-4c2c-9a32-7329b7b056ec" />


### Step 2: Review the Order Summary

The top of the page shows a read-only summary pulled from EasyStore:

- Order number (e.g. #1001)
- Customer name and delivery address
- Number of items and total weight

**Ship from (multi-region stores only):** if you have more than one region, a **Ship from** selector appears. The app pre-selects the region that matches the order's pickup location (falling back to your default region). Use the selector to change which EasyParcel account/region ships this order.

<img alt="Screenshot 2026-07-01 at 3 36 38 PM" src="https://github.com/user-attachments/assets/8ba2cfb6-b914-41ea-bcc1-f48d501b9fd6" />


### Step 3: Set Parcel Details

| Field | Description |
|---|---|
| Pickup Date | Date you want EasyParcel to collect the parcel. Defaults to the next day. |
| Delivery Option | **Pickup** (EasyParcel collects from you) or **Drop off** (you deliver to a collection point) |
| Drop-off Point | Only shown when "Drop off" is selected. Choose a nearby collection point. |
| Use custom weight & dimension | Toggle on to override with your actual measured weight (kg) and dimensions. Minimum weight 0.01 kg. |
| Dimensions | Length × Width × Height in cm. Pre-filled from product data if available; editable when custom weight is on. |
| Declared Value | The declared value of the parcel. Defaults to the order subtotal. |
| Parcel content | Choose **SKU** or **Product name** for the parcel content. Pre-selected from your [Default Parcel Content](#47-default-parcel-content) setting. In bulk fulfillment this choice applies to all orders in the batch. |
| Parcel Category | Select the category that best describes your product (e.g. Documents, Electronics, Apparel), from the categories offered by EasyParcel for that region. |
| HS Code | Shown for international orders only. Required for customs clearance. |
| SMS Notification | Toggle on to send the recipient an SMS. |

<img alt="Screenshot 2026-06-23 at 5 50 09 PM" src="https://github.com/user-attachments/assets/a62609ae-9271-40f6-ad5b-dbdd955582fd" />
<img alt="Screenshot 2026-06-23 at 5 52 37 PM" src="https://github.com/user-attachments/assets/7f9716e7-120d-40cc-bce8-f46cd88215b5" />


### Step 4: Get a Rate Quote

The app queries EasyParcel and displays available courier options with prices and estimated delivery times.
<img alt="image" src="https://github.com/user-attachments/assets/b893f5e9-60cc-4fb6-8b6b-2b8af376468e" />
<img alt="Screenshot 2026-06-24 at 9 50 33 AM" src="https://github.com/user-attachments/assets/a6e3350d-3d14-4850-a979-ef42c6b8310a" />

Each rate shows:
- Courier logo and name (e.g. Pos Laju)
- Service name (e.g. Pos Laju Prepaid)
- Estimated delivery time
- Price

Select the rate you want by clicking the radio button next to it. The app pre-selects a sensible default (your saved default courier, or the option the customer chose at checkout, or the cheapest available).

### Step 5: Confirm the Booking

Click **[Fulfill now]**. In a single step the app will:

1. Book the parcel with EasyParcel
2. Pay for the parcel using your EasyParcel balance
3. Update the order on EasyStore with the tracking number
<img alt="image" src="https://github.com/user-attachments/assets/be9fffb6-50d9-4123-812a-be79166ba7d9" />
<img alt="image" src="https://github.com/user-attachments/assets/13affe53-c32e-47a4-b2fc-a13e332c4aec" />

**Insufficient balance?**  
If your EasyParcel credit balance is too low, the booking fails at the payment step and the completion screen reports "Payment failed — insufficient credit." (in bulk fulfillment, the affected order is listed under **Failed**). Top up your balance on the EasyParcel dashboard, then try again.

### Step 6: View the Result

After a successful fulfillment, the success screen shows:

- Tracking number
- Courier and service name
- Tracking URL (clickable link)
- **[Download Air Waybill]** button
<img alt="Screenshot 2026-06-24 at 9 59 29 AM" src="https://github.com/user-attachments/assets/5ffd111f-f6e9-43a6-889b-17ed19af3d4e" />
<img alt="Screenshot 2026-06-24 at 10 03 25 AM" src="https://github.com/user-attachments/assets/c0229591-a3d0-4afc-86a7-db18324e6834" />



The EasyStore order timeline is automatically updated with the tracking number and courier details.

---

## 6. Fulfilling Multiple Orders at Once (Bulk)

Bulk fulfillment works the same as single order fulfillment (see [Section 5](#5-fulfilling-an-order)), with a few differences in how you start it and review the result.

### Step 1 — Select Orders in EasyStore

1. Go to EasyStore admin → **Orders**
2. Tick the checkboxes next to the orders you want to fulfill
3. Click **Fulfill** → select **Fulfill with EasyParcel**

EasyStore opens the bulk fulfillment page inside your admin.

<img alt="Screenshot 2026-06-24 at 10 10 42 AM" src="https://github.com/user-attachments/assets/3e11acda-0e21-479a-912a-c20373791dbc" />


### Step 2 — Review Selected Orders

Instead of a single order summary, the page header shows the total number of orders being fulfilled and lists all order numbers (e.g. #1001, #1002, #1003). The parcel details, rate quote, and confirm steps are the same as single fulfillment — the settings you enter apply to all orders in the batch.

> **Multi-region note (bulk only):** if your selected orders belong to more than one region, a banner appears: *"Orders span multiple regions. All will ship from {region}. Use the Ship from selector to change."* All orders in the batch ship from the region shown in the **Ship from** selector — change it if needed.

<img alt="Screenshot 2026-06-24 at 10 13 39 AM" src="https://github.com/user-attachments/assets/d2849d97-ee8a-410b-a9b7-88789be50e87" />


### Step 3 — Fulfill and Review Results

Follow **Steps 3 to 5** from [Section 5](#5-fulfilling-an-order). After you confirm, the completion screen shows a summary ("X of Y fulfillments created successfully") with a **Successful** table (order numbers, tracking numbers, couriers) and, if any failed, a **Failed** table with the reason.

Click **[Download All AWBs]** to get a single merged PDF containing labels for all successfully fulfilled orders.

<img alt="Screenshot 2026-06-24 at 10 17 17 AM" src="https://github.com/user-attachments/assets/50d9a299-0811-4a56-8433-b79cdb960b3f" />


---


## 7. Printing Air Waybills (AWB)

The Air Waybill (AWB) is the shipping label you attach to your parcel before handing it to the courier. You can print in **A4** or **4"×6" sticker** format — pick the format on the AWB page.

---

### 7.1 Single Order AWB

#### From the Fulfillment Success Screen

Click **[Download Air Waybill]** immediately after fulfillment. The AWB opens in a new browser tab as a PDF.

#### From an Existing Order (Reprint)

1. Go to EasyStore admin → **Orders** → open the fulfilled order
2. Click **More actions** → select **Download EasyParcel AWB**

The AWB page opens inside EasyStore admin. Choose **A4** or **4"×6" sticker**, then preview/download.

<img alt="image" src="https://github.com/user-attachments/assets/08ad9676-ced1-4ad4-b097-6eed6d8ea97e" />


---

### 7.2 Bulk AWB Download

After bulk fulfillment you can download all AWBs as a single merged PDF — one print job covers all your labels.

#### From the Bulk Fulfillment Completion Screen

Click **[Download All AWBs]** on the bulk fulfillment completion screen (see [Section 6 — Step 3](#step-3--fulfill-and-review-results)).

#### From Existing Orders (Reprint)

1. Go to EasyStore admin → **Orders**
2. Tick the checkboxes next to the fulfilled orders
3. Click **Print** → select **Download EasyParcel AWB**

The bulk AWB page opens, generates each label, and merges the available ones into a single PDF.

<img alt="image" src="https://github.com/user-attachments/assets/fbec56b3-3c11-4f46-84e0-1632df85113e" />

> **Note:** If some selected orders can't be downloaded (for example they weren't fulfilled via EasyParcel, or their label isn't ready yet), the page lists those orders with the reason and still lets you download the ones that are available.

> **Orders fulfilled in the older MY/SG apps:** AWBs for orders booked through this app use that order's saved region account. For older orders booked before the app was consolidated, the app automatically checks each of your configured EasyParcel accounts to find and fetch the label.

---

## 8. Tracking Parcel Status

Once an order is fulfilled, the app automatically keeps your EasyStore order timeline up to date — no manual action required.

### How It Works

EasyParcel **pushes** each status change to the app in real time (as soon as the courier scans the parcel), and the app immediately updates the order timeline in EasyStore. There's no waiting for a scheduled check.

### Parcel Status Stages

| Status | Meaning |
|---|---|
| Pending | Parcel booked, waiting for EasyParcel pickup |
| In Transit | EasyParcel has collected the parcel and it is moving |
| Out for Delivery | Parcel is on the delivery vehicle |
| Delivered | Parcel delivered to the recipient |
| Failed | Delivery attempt failed |
| Returned | Parcel returned to sender |
| Cancelled | Shipment cancelled |

### Customer Notifications

When the parcel status reaches **Delivered**, EasyStore automatically sends a notification email to your customer. This is handled by EasyStore — you do not need to do anything.

### Viewing Tracking on an Order

1. EasyStore admin → **Orders** → open the fulfilled order
2. The order timeline shows the current status and tracking number
3. Click the tracking URL to view the full EasyParcel tracking page

<img alt="Screenshot 2026-06-24 at 10 28 12 AM" src="https://github.com/user-attachments/assets/86c0aab2-5741-4e1a-b18f-b7dc17798777" />


---

## 9. Uninstalling the App

To remove the app from your store:

1. EasyStore admin → **Apps** → **EasyParcel Malaysia** → **Uninstall**

Your settings, fulfillment history, and tracking logs are **retained**. If you reinstall the app in the future, you only need to re-authorize with EasyStore — all your previous settings (including every region) will still be there.

---

## 10. Troubleshooting

### No shipping rates appear at checkout

Check the following in Settings, for the relevant region:

1. **Integration ID** is entered and validated (balance badge should be visible)
2. **Enable EasyParcel Rate** toggle is ON
3. A **Pickup Location** is selected under Company Information
4. Your origin address (pickup location) is a valid address with a correct postcode
5. The courier isn't hidden under **Exclude Couriers from Checkout Rates**

If all of the above are correct, check if you have a **Fallback Rate** configured so customers always see at least one shipping option.

---

### "Invalid integration ID. Please double check."

Your Integration ID failed verification. Confirm that:
- You selected a **pickup location** first (the app needs the region to verify against the correct EasyParcel service)
- You copied the ID without extra spaces
- Your EasyParcel account is active and not suspended
- You are using the Integration ID (API key), not your EasyParcel login password

---

### Fulfillment fails with "Payment failed — insufficient credit."

Your EasyParcel wallet does not have enough credit to pay for the shipment. Top up your balance at [EasyParcel Dashboard](https://www.easyparcel.com), then try fulfilling the order again.

---

### AWB download shows "This order was not fulfilled by EasyParcel."

This order was not fulfilled using EasyParcel (it may have been fulfilled manually or via another app), so there is no EasyParcel label to download. If the order *was* fulfilled through EasyParcel but you still see this, confirm the correct region's EasyParcel account is configured in Settings.

---

### Checkout shows rates but they seem too high

Check your handling fee and percentage settings in the Settings page (for the relevant region):
- **Handling Fee** — a flat fee added to every rate
- **Percentage** — a percentage adjustment on top (a positive value marks the rate up)

Reduce or clear these fields if you don't want any markup.

---

### Tracking status hasn't updated

Tracking updates are pushed by EasyParcel in real time. If a status looks stale:
1. Check the EasyParcel tracking page directly (the tracking URL is on the order timeline)
2. If EP tracking shows a newer status than EasyStore, contact support — a status push may have been missed and can be re-synced manually.

---

*For further help, visit the [EasyStore Help Centre](https://support.easystore.co) or contact EasyParcel support.*
