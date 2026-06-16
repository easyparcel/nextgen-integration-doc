# Malaysia E-Invios Setup(Shopify)
With the integration of LHDN MyInvois, EasyParcel acts as an intermediary to help you generate, validate, and store e-Invoices directly from your Shopify platform.  

By completing this setup, your invoices will be automatically submitted to **LHDN** for validation once an order is **fully fulfilled** — whether fulfilled through the **EasyParcel** app or marked as **Fulfilled** in Shopify — ensuring compliance with Malaysia's e-Invoice requirements while simplifying your business operations. (Auto-submission applies to **MYR** orders and runs **once per order**.)

## Navigation path
**Login your Shopify Store -> Apps -> EasyParcel -> Settings -> E-Invoice Profile**

**Step 1:** Fill in all fields marked with **"*"**, as they are compulsory. Then, click the **"Update"** button to ensure your information is saved. After that, click **"Enable Auto Submit E-Invoice to LHDN"** if you wish to enable this feature.
<img width="100%" alt="image" src="https://github.com/user-attachments/assets/6d63c108-1d63-49ef-a46a-fb058ca9a566" />
<img width="100%" alt="image" src="https://github.com/user-attachments/assets/e6e91fcb-fadb-429b-ad75-9479d5de137a" />


**Step 2:** Follow the steps shown in the image. Once completed, click the **"Done Setting, Continue to Verification"** button.  

Once this feature is enabled, the system will automatically submit invoices to your **MyInvois** account once an order is fully fulfilled — whether through the **EasyParcel** app or marked as **Fulfilled** in Shopify.
<img width="100%" alt="Screenshot 2026-06-16 at 2 32 58 PM" src="https://github.com/user-attachments/assets/96ddff06-8496-45ab-940f-227f17c541c1" />


Now, you are able to use the auto submit E-invoice to LHDN feature.
<img width="100%" alt="Screenshot 2026-06-16 at 2 33 52 PM" src="https://github.com/user-attachments/assets/7afe6d22-d91f-4223-b9bf-cf602f2493f1" />


> **How auto-submit works:** it sends the e-Invoice **once per order**, only when the order is **fully fulfilled** (not on partial fulfilments), and only for **MYR** orders. If a buyer provided their details at checkout, the invoice is issued to that buyer; otherwise it is submitted as general public. If a submission fails, you can retry it manually from the order page (see below).

---

# Default Classification Code

Every line item submitted to LHDN needs a **classification code**. Instead of setting it on every order, you choose a default once in your **E-Invoice Profile** (the same form as **Step 1** above). It defaults to **`008` (e-Commerce)** and is required.
<img width="100%" alt="image" src="https://github.com/user-attachments/assets/4f294329-5531-49fc-b842-6f1adaa98e98" />


**How it is used:**
- The selected code becomes the default for **every line item** (products and shipping) on every order.
- Classification codes are only sent to LHDN **when buyer details are submitted** for the order. If there are **no buyer details**, the e-Invoice is submitted as **general public (Consolidated)** using classification code `004`.
- You can still **override the code per item** on the order page (see *Manual / Retry Submit E-Invoice* below).

---

# Buyer E-Invoice at Checkout

Your buyers can optionally request an e-Invoice during checkout and enter their own tax details (TIN, ID, name, address, etc.). When provided, those details are issued on the e-Invoice instead of *general public*.

On Shopify this is enabled by **adding the EasyParcel e-invoice block to your checkout** (there is no on/off toggle in the profile):

## Add the block to your checkout
**Login your Shopify Store -> Settings -> Checkout -> Edit**
<img width="100%" alt="Screenshot 2026-06-16 at 3 13 56 PM" src="https://github.com/user-attachments/assets/329b2006-9c09-4c83-9eed-3f4f981460ff" />


1. In the checkout editor, add the **EasyParcel E-Invoice Buyer Details** app block (e.g. just after the **Contact** section).
   <img width="100%"  alt="Screenshot 2026-06-16 at 3 27 31 PM" src="https://github.com/user-attachments/assets/6663a790-e970-4e50-9fa9-3006b43d4c4e" />

   
3. Turn on **"Allow app to block checkout"** so the required fields are enforced. Click **Save** so the block goes live on your checkout.
   <img width="100%" alt="Screenshot 2026-06-16 at 3 28 24 PM" src="https://github.com/user-attachments/assets/f20d6d3f-d7eb-40f7-ae46-d815e772cd19" />


If you don't add the block, checkout is unaffected and every order is submitted as general public.

### What the buyer sees at checkout
An **"I want a Malaysia LHDN e-invoice (add buyer details)"** checkbox appears after the contact section. Requesting an e-Invoice is **optional** — the buyer decides whether to submit their details. When the buyer ticks it, the following fields appear:

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


**Sample Checkout Page**
<img width="100%"  alt="image" src="https://github.com/user-attachments/assets/cdf8d210-902b-4021-8f98-df10317885ff" />

- If the buyer leaves the checkbox unticked, the order is submitted as general public.
- All fields except **SST** are required once the buyer opts in; checkout is blocked until they are completed (this requires **"Allow app to block checkout"** to be enabled on the block).


---

# Manual / Retry Submit E-Invoice (Order Page)

Every Malaysia order has a collapsible **EasyParcel E-Invoice (Malaysia)** section on its order details page (click the header to expand). Use it to submit the e-Invoice manually, or to **retry** after a failed submission — optionally editing the details first. This is useful when a submission needs correcting.

## Navigation Path:
**Login your Shopify Store -> Apps -> EasyParcel -> Orders -> (open an order) -> EasyParcel E-Invoice (Malaysia)**
<img width="100%" alt="Screenshot 2026-06-16 at 3 45 40 PM" src="https://github.com/user-attachments/assets/0ce4fd26-6634-409c-ba15-2c4ff203aabd" />
<img width="100%" alt="Screenshot 2026-06-16 at 3 46 12 PM" src="https://github.com/user-attachments/assets/6f2f69fd-6802-40fe-89d6-49248650a59e" />


The panel shows:

- **Status** — *Submitted*, *Failed*, or *no e-invoice submitted yet*.
- **Last submitted** — date/time of the most recent submission attempt.
- **Last remark** — the result message from the most recent submission attempt.
- **Submit buyer details** toggle with editable buyer fields.
- **Item table** — each product and the shipping fee, with their amount, tax, and an editable **classification code**.
- **"Submit E-Invoice" / "Retry Submit E-Invoice"** button.

### When to use it

- **Auto-Submit enabled:** e-Invoices are sent automatically once an order is fully fulfilled. You normally only use this panel to **retry** a failed submission.
- **Auto-Submit disabled:** use this panel to submit the e-Invoice **manually**.

(The panel shows a banner reminding you which mode you're in.)

### Editing before you submit / retry

**Step 1:** **Buyer details** — tick **"Submit buyer details"** to issue the e-Invoice to a specific buyer, then complete the fields. Leave it unticked to submit as general public.
- When ticked, all fields except **SST** are required; submission is blocked until they are complete.

**Step 2:** **Classification code** — each item (and the shipping fee) defaults to your profile's **Default Classification Code**. Change any row's dropdown to override it for this order.

**Step 3:** Click the **"Submit E-Invoice"** / **"Retry Submit E-Invoice"** button.

> Non-MYR orders cannot be submitted — the panel shows a notice and the controls are disabled.

### Result

- On success, the status updates to **"Submitted"**. This means the document has been **submitted to EasyParcel successfully**. EasyParcel stores it and submits it to LHDN for validation in the background, so the status reflects a successful submission to EasyParcel — not the final LHDN validation result.
- If the submission was not accepted, the **Last remark** shows the message so you can correct the details and retry.

---

# Frequently Asked Questions

**Do I have to enable buyer details to submit e-Invoices?**
No. Without buyer details (or if the buyer doesn't provide them), orders are still submitted as general public.

**The buyer e-Invoice fields don't appear at checkout. Why?**
Confirm all of these: your store country is **MY**, an **E-Invoice Profile** exists, and you have **added the EasyParcel e-invoice block in the checkout editor and published** it. For the required-field validation to block checkout, also enable **"Allow app to block checkout"** on the block.

**Why does my item show a different classification code than my profile?**
The order has a per-item override set previously. Set the item's dropdown back to your profile's default code and submit again to clear the override.

**Can I submit again if the first attempt failed?**
Yes — fix the details in the order panel and click **"Retry Submit E-Invoice"**. Auto-submit only runs **once per order**, so failed auto-submissions are retried here.

**When exactly does auto-submit fire?**
Once an order becomes **fully fulfilled** — via EasyParcel or marked as Fulfilled in Shopify — for **MYR** orders, and only **once per order**. Partial fulfilments do not trigger it.
