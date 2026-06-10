# Malaysia E-Invios Setup(Woocommerce)
With the integration of **Lembaga Hasil Dalam Negeri Malaysia (LHDN) MyInvois**, EasyParcel acts as an intermediary to help you generate, validate, and store e-Invoices directly from your WooCommerce platform.

By completing this setup, your invoices will be automatically submitted to LHDN for validation whenever an order is fulfilled through the EasyParcel plugin integration in your Woocommerce Store, ensuring compliance with Malaysia's e-Invoice requirements and simplifying your business operations.

## Navigation Path:
**Login your Woocommerce store -> Woocommerce -> Settings -> Shipping -> E-Invoice Profile**

**Step 1:** Fill in the required information in the text boxes. Fields marked with **"*"** are compulsory, while the others are optional.
<img width="100%" alt="Screenshot 2026-03-17 at 2 46 53 PM" src="https://github.com/user-attachments/assets/7771084b-adb7-41f6-9653-687894bc49a1" />

**Step 2:** Click the **"Update"** button to update the information that you have filled in.
<img width="100%" alt="image" src="https://github.com/user-attachments/assets/9fa18aed-e903-4e55-87fd-4b761d18f976" />


**Step 3:** Click **"OK"** if you want the system to automatically update and submit invoices to your **MyInvois** account whenever an order is fulfilled through the **EasyParcel** plugin integration. Otherwise, click **"Cancel."**
<img width="100%" alt="Screenshot 2026-03-17 at 2 48 11 PM" src="https://github.com/user-attachments/assets/a78e158c-54c5-40bf-93e1-6612d28ebffa" />

**Step 4:** If you click **"Ok"** in the previous step, Follow the steps in the image, once done click the **"Done Stting, Continue to Verification"** button.
<img width="100%" alt="Screenshot 2026-03-17 at 2 48 39 PM" src="https://github.com/user-attachments/assets/99e4e268-7641-4148-b9a4-6b3b9ffb44f8" />

**Step 5:** The success message will be pop out.
<img width="100%" alt="Screenshot 2026-03-17 at 2 49 00 PM" src="https://github.com/user-attachments/assets/77c8b882-9e7e-4f74-abb0-bd00125145dc" />

**Step 6:** The **"Enabled"** badge will displayed on top if it is enabled.
<img width="100%" alt="Screenshot 2026-03-17 at 2 49 34 PM" src="https://github.com/user-attachments/assets/b72e13dd-8808-47ca-b69f-34b9dbf8a0b8" />

---

# Default Classification Code

Every line item submitted to LHDN needs a **classification code**. Instead of setting it on every order, you choose a default once in your **E-Invoice Profile** (the same form as **Step 1** above).
<img width="100%" alt="image" src="https://github.com/user-attachments/assets/dec7e24b-1ba6-4a2b-b775-5a692404f911" />

**How it is used:**
- The selected code becomes the default for **every line item** (products and shipping) on every order.
- It applies when **buyer details are submitted** for the order. If there are **no buyer details**, the e-Invoice is treated as consolidated / general public and classification code **`004` (Consolidated e-Invoice)** is used by default.
- You can still **override the code per item** on the order page (see *Manual / Retry Submit E-Invoice* below).

---

# Buyer E-Invoice at Checkout

When enabled, your buyers can choose to request an e-Invoice at checkout and enter their own tax details (TIN, ID, name, address, etc.). Those details are then issued on the e-Invoice instead of *general public*. When unticked, no e-Invoice fields appear at checkout and every order is submitted as general public (the original behaviour).
<img width="100%" alt="image" src="https://github.com/user-attachments/assets/19f74608-eac5-47f7-aa3b-021dfec2da8e" />


### What the buyer sees at checkout
<img width="100%" alt="image" src="https://github.com/user-attachments/assets/df1ace69-7772-44f0-9582-38688549aae8" />


An **E-Invoice (Malaysia)** section appears with a **"Request e-invoice (Malaysia LHDN)"** checkbox. Requesting an e-Invoice is **optional** — the buyer decides whether to submit their details. When the buyer ticks it, the following fields appear:

| Field | Required |
|---|---|
| Buyer / Company Name | Yes |
| Tax Identification Number (TIN) | Yes |
| SST Registration Number | No (optional) |
| ID Type (BRN / NRIC / Army ID / Passport) | Yes |
| ID Number | Yes |
| Phone | Yes |
| Address | Yes |
| City | Yes |
| Postcode | Yes |
| State | Yes |

<!-- screenshot: checkout e-invoice fields -->

- If the buyer leaves the checkbox unticked, the order is simply submitted as general public.
- All fields except **SST** are required once the buyer opts in; checkout is blocked until they are completed.
- Works on **both** the classic checkout and the new **Checkout block**.

### Saved for next time

For **logged-in** customers, the details are remembered and **pre-filled automatically** on their next checkout, so they don't need to re-type them. (Guests are not pre-filled, as there is no account to save against.)

---

# Manual / Retry Submit E-Invoice (Order Page)

Every Malaysia order has an **EasyParcel E-Invoice (Malaysia)** panel on its order details page. Use it to submit the e-Invoice manually, or to **retry** after a failed submission — optionally editing the details first. This is useful when a submission needs correcting.

## Navigation Path:
**Login your Woocommerce store -> Woocommerce -> Orders -> (open an order) -> EasyParcel E-Invoice (Malaysia)**
<img width="100%" alt="Screenshot 2026-06-10 at 12 52 23 PM" src="https://github.com/user-attachments/assets/13063c36-5772-46cf-84df-afc3558d154f" />
<img width="100%" alt="image" src="https://github.com/user-attachments/assets/3127338d-a839-42df-bded-a29d97d8a354" />


The panel shows:

- **Status** — *Submitted* (with the invoice number), *Failed*, or *Not submitted*.
- **Last submitted** — date/time of the most recent submission attempt.
- **Last remark** — the result message from the most recent submission attempt.
- **Buyer E-Invoice Details** — editable buyer fields with a *"Submit buyer details"* toggle.
- **Item table** — each product and the shipping fee, with their amount, tax, and an editable **classification code**.
- **"Retry Submit E-Invoice"** button.

<!-- screenshot: e-invoice order panel -->

### When to use it

- **Auto-Submit enabled:** e-Invoices are sent automatically after fulfilment. You normally only use this panel to **retry** a failed submission.
- **Auto-Submit disabled:** use this panel to submit the e-Invoice **manually**.

(The panel shows a banner reminding you which mode you're in.)

### Editing before you retry

**Step 1:** **Buyer details** — tick **"Submit buyer details"** to issue the e-Invoice to a specific buyer, then complete the fields. Leave it unticked to submit as general public.
- When ticked, all fields except **SST** are required; the retry is blocked until they are complete.

**Step 2:** **Classification code** — each item (and the shipping fee) defaults to your profile's **Default Classification Code**. Change any row's dropdown to override it for this order.
- Selecting the same value as the profile default removes the override, so the item simply follows the profile again.

**Step 3:** Click the **"Retry Submit E-Invoice"** button.
<!-- screenshot: editable buyer details + item classification -->

### Result

- On success, the status updates to **"Submitted"** with the invoice number. This means the document has been **submitted to EasyParcel successfully**. EasyParcel stores it and submits it to LHDN for validation in the background, so the status reflects a successful submission to EasyParcel — not the final LHDN validation result.
- If the submission was not accepted, the **Last remark** shows the message so you can correct the details and retry.

---

# Frequently Asked Questions

**Do I have to enable buyer details to submit e-Invoices?**
No. With buyer details disabled (or not provided by the buyer), orders are still submitted as general public — the original behaviour.

**The buyer e-Invoice fields don't appear at checkout. Why?**
Confirm all three conditions: sender country is **MY**, an **E-Invoice Profile** exists, and **Buyer E-Invoice at Checkout** is ticked in the profile.

**Why does my item show a different classification code than my profile?**
The order has a per-item override set previously. Set the item's dropdown back to your profile's default code and Retry to clear the override.

**Can I submit again if the first attempt failed?**
Yes — fix the details in the order panel and click **"Retry Submit E-Invoice"**. The *Last remark* shows the message from the last attempt.
