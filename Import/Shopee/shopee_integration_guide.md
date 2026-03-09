# EasyParcel Shopee NextGen Integration

---

## Introduction
This guide will walk you through integrating NextGen EasyParcel with Shopee. With this integration, you'll import orders from Shopee into your EasyParcel account for fulfillment.

---
## What is Non‑Shopee Supported Logistics (Non‑SSL)?
1. Non‑SSL refers to logistics providers not officially integrated with Shopee, such as EasyParcel.
2. Orders must be manually booked in the external system, and tracking numbers manually or automatically updated back to Shopee.
3. Some automated features (like waybill printing or direct Shopee tracking display) may not function the same as SSL.

## What is Shopee Supported Logistics (SSL)?
1. SSL refers to logistics providers that are officially supported and integrated by Shopee (e.g., Pos Laju, Shopee Xpress, J&T Express).
2. Orders with SSL can automatically print waybills, sync tracking numbers, and shipping fees are settled directly through Shopee.
3. SSL is suitable for standard Shopee orders, offering automated processes, full tracking, and simplified workflow.

## Comparison
| Feature          | Shopee Supported Logistics (SSL) | EasyParcel (Non‑SSL)                     |
| ---------------- | -------------------------------- | ---------------------------------------- |
| Fee settlement   | Paid through Shopee              | Deducted from EasyParcel account balance |
| Tracking display | Automatically in Shopee          | Tracking synced back after booking       |
| Waybill printing | Directly in Shopee               | Must print in EasyParcel                 |


## Requirement
Before integrating your Shopee store with EasyParcel, please ensure that the following requirement are met:
### 1. Must Apply for “Other Logistics Provider” in Shopee Seller Centre
Before you can integrate EasyParcel and fulfil orders with Non‑SSL logistics, you must submit an application to Shopee for the Non‑Shopee Supported Logistics (Other Logistics Provider) option. Shopee must approve this application before you can connect EasyParcel to your store.

[guideline for register non-SSL Application](https://seller.shopee.com.my/edu/article/16238)

[FAQ Non-SSL](https://seller.shopee.com.my/edu/article/26364)

### 2. Meet Shopee’s Eligibility Criteria for Non‑SSL Logistics
Shopee’s platform has conditions for allowing Non‑SSL logistics:

✔ Provide Business Registration Documents (e.g., trading license like SSM in Malaysia). Sellers often need to submit valid proof.

✔ Provide reasons for using Non‑SSL logistics (e.g., selling bulky items that Shopee’s supported couriers can’t handle, special delivery needs, etc.) — this makes your application more likely to be approved.

✔ Maintain good seller performance — Shopee may revoke Non‑SSL access if performance standards drop or if no Non‑SSL orders occur in a period of time.


## 3. Once Approved, Integrate Your Shopee Account with EasyParcel
#### **Step 1:** Under EasyConnect section, click on "Add Ecommerce App", find "Shopee" and click on "Install App"

<img width="1280" height="725" alt="image" src="https://github.com/user-attachments/assets/72a73b67-5dcb-4b02-b6e0-eeb6e5336d13" />

---

#### **Step 2:** Click on the "Allow Access" button

<img width="1280" height="650" alt="image" src="https://github.com/user-attachments/assets/573ead2c-523d-4130-8ae1-a82deb11197d" />

---

#### **Step 3:** Key in your "Store Name" and "Store URL" and click on the "Connect" button

<img width="1280" height="659" alt="image" src="https://github.com/user-attachments/assets/da9b4e9d-33c1-492b-b527-50dcb22a40f2" />

---

#### **Step 4:** Log in into your Shopee account

<img width="1280" height="699" alt="image" src="https://github.com/user-attachments/assets/cd51e8f5-3490-44b2-88d7-d86977fc0526" />

---

#### **Step 5:** Click on "Confirm Authorization" button

<img width="1280" height="574" alt="image" src="https://github.com/user-attachments/assets/09b54793-10f6-4d4e-94e7-d68da8ae03ab" />

---

#### **Step 6:** Under "EasyConnect", click on "Installed Ecommerce Apps", find "Shopee" and click on "Open App" button

<img width="1280" height="647" alt="image" src="https://github.com/user-attachments/assets/3b700fe5-8640-40bf-94df-b2b6a7635087" />

---

#### **Step 7:** In the store, click "Sender Address" and key in your sender details and click on the "Update" button

<img width="1280" height="655" alt="image" src="https://github.com/user-attachments/assets/a9def365-2783-4387-8353-383d1a337aeb" />

---

#### **Step 7:** Click on "Order", select the order date and order status and click on the "Search" button. The order will be imported and shown in the list below. Then, click the "Fulfill" button on the order you want to fulfill

<img width="1280" height="665" alt="image" src="https://github.com/user-attachments/assets/a9adb6e8-aa23-4b59-b172-2c531e64790b" />

---
## Conclusion
You've successfully set up EasyParcel Shopee integration using the Import Version! You will now can fulfill orders after importing to EasyParcel NextGen website.

**You may proceed to checkout our [Shopee Import Fulfilment Steps](https://github.com/easyparcel/nextgen-integration-doc/blob/c33489763a3b572fc0d09f01d6b84e72328a62f8/Import/Shopee/shopee_fulfilment.md)**

If you have any questions or need further assistance, [check out our other articles](https://helpcentre-my.easyparcel.com/support/home) or reach out to our friendly support team. We're happy to help you every step of the way! 
