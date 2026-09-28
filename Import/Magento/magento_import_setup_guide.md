# EasyParcel Magento NextGen Integration - Import version
---
## Introduction
This guide will walk you through integrating NextGen EasyParcel with Magento 2 using the Import Version method. With this integration, you'll import orders from Magento into your EasyParcel account for fulfilment, and EasyParcel sends the tracking number back to Magento when you ship.

Nothing needs to be installed on your Magento store. You only create an **integration** in your Magento admin and copy four values from it into EasyParcel.

> ℹ️ Works with Magento Open Source 2.4.6 and later. You need a Magento admin account that can manage integrations.

---

## How to access to NextGen EasyParcel
**Step 1:** [Log in to your EasyParcel account](https://account.easyparcel.com/login?client_id=c575e8cd-aa46-46db-8308-e18d25bb76c6&redirect_uri=https%3A%2F%2Fapp.easyparcel.com%2Feasyaccount%2Fcallback&state=eyJjbGllbnRfaWQiOiI1M2FmYmQzMS05OGI2LTQ3ODctOWYzOC1kMDY5ZGRkN2RiM2QiLCJyZWRpcmVjdF91cmkiOiJodHRwczovL2FwcC5lYXN5cGFyY2VsLmNvbS9sb2dpbi9vYXV0aC9jYWxsYmFjayIsInN0YXRlIjoie30iLCJjb3VudHJ5IjoibXkiLCJsYW5nIjoiZW4ifQ%3D%3D&country=my)



## Set Up Magento Import Integration

#### **Step 1:** In the menu, under "Integration", click on "Add Ecommerce App", find "Magento" and click on "Install App"

<img alt="02-add-ecommerce-app" src="https://github.com/user-attachments/assets/2f65780f-033a-4748-849c-33f883fdc0f3" />


#### **Step 2:** Key in your "Store Name" and "Store URL" and click on the "Connect" button.

Use your store's **website address** (for example `https://www.yourstore.com`), not the address of your Magento admin page.

<img alt="03-store-name-url" src="https://github.com/user-attachments/assets/99e925a7-41e1-44fd-afb0-3dbb43c4eba8" />



#### **Step 3:** Key in your "Consumer Key", "Consumer Secret", "Access Token" and "Access Token Secret" and click on the "Submit" button.

EasyParcel asks for four values. You create them in your Magento admin:

  1. In your Magento admin, go to **System > Extensions > Integrations** and click **Add New Integration**.
     <img alt="04-magento-integrations" src="https://github.com/user-attachments/assets/2f3aa6d4-a2b9-439c-b454-885a1bfe0221" />


  3. On the **Integration Info** tab, give it a name (for example "EasyParcel"), then enter your own Magento admin password under **Your Password**.
     <img alt="05-integration-info" src="https://github.com/user-attachments/assets/477a847a-4988-4b7e-aa91-56ad6263965c" />


  3. Open the **API** tab. Keep **Resource Access** as **Custom** and tick only these four:
     - **Sales > Operations > Orders > Actions > View**
     - **Sales > Operations > Orders > Actions > Ship**
     - **Sales > Operations > Shipments**
     - **Stores > Settings > All Stores**

     This lets EasyParcel read your orders and add shipments with tracking numbers. It cannot see your customer accounts or change your products, prices or store settings.
     <img alt="06-api-permissions" src="https://github.com/user-attachments/assets/93a9f565-63dd-4b24-b0e9-cfe55513374a" />



> 💡 **Optional — parcel dimensions.** To send each product's length, width and height to EasyParcel, also tick **Catalog > Inventory > Products**. Your products need attributes named *length*, *width* and *height* (in cm). Magento also lets this permission edit products; EasyParcel only reads the dimensions. Without it, your default parcel size is used.
  <img alt="07-optional-products-permission" src="https://github.com/user-attachments/assets/8d31bc74-090a-4209-93b2-04cbcc3e9e9e" />


  4. Click **Save**. Back on the Integrations list, click **Activate** next to your new integration, then click **Allow**.
     <img alt="08-activate-allow" src="https://github.com/user-attachments/assets/1ca38802-1b4d-4f7f-90df-93552fad7a9c" />


  6. Magento now shows the four values: **Consumer Key**, **Consumer Secret**, **Access Token** and **Access Token Secret**. Copy each one.
     <img alt="09-integration-tokens" src="https://github.com/user-attachments/assets/83b380ed-9b9a-47c8-8c7b-b9c718b0ada1" />

> 🔒 Keep these four values private, like a password. You can find them again any time under **System > Extensions > Integrations** → your integration → **Integration Details**.

There, you may go back to EasyParcel portal to fill in the four values and press **Submit**.
<img alt="10-enter-credentials" src="https://github.com/user-attachments/assets/afcf9c25-1ec7-45ee-aabb-6900375ef1ec" />


> ⚠️ If EasyParcel shows an error instead, it tells you which value to check. For example, "did not recognise the Consumer Key", or "missing this permission: Sales > Operations > Orders > Actions > Ship". To fix a permission, edit the integration in Magento, tick it and click **Save**. Your four values stay the same, so enter them again and submit.

#### **Step 4:** Under "Integration", click on "Installed Ecommerce Apps". You will find your Magento app installed there.
<img alt="11-installed-apps" src="https://github.com/user-attachments/assets/569775e6-2fa1-45d9-993b-cbfa74640e32" />



#### **Step 5:** Click "Open App" on Magento, then click into your store. Open the "Sender Address" tab, key in your sender details and click on the "Update" button.
<img alt="12-sender-address" src="https://github.com/user-attachments/assets/4ce7d3cc-5d3a-4e41-92e9-d29c91ac1232" />


#### **Step 6:** Open the store's "Settings" tab, adjust the settings based on your preference and click the "Update" button at the bottom of the page.

With **Auto order status update** on, when you fulfil an order EasyParcel creates the **shipment** on your Magento order with the tracking number, and Magento emails your customer its usual shipment email.
<img alt="13-auto-update-setting" src="https://github.com/user-attachments/assets/11e0d90a-24bf-4a7b-9902-c66a69819e47" />


#### Done ! You have successfully setup Magento import app in easyparcel.

## Conclusion
You've successfully set up EasyParcel Magento integration using the Import Version! You will now can fulfil orders after importing to EasyParcel NextGen website.

**You may proceed to checkout our [Magento Import Fulfilment Steps](./magento_import_fulfilment.md)**

If you have any questions or need further assistance, [check out our other articles](https://helpcentre-my.easyparcel.com/support/home) or reach out to our friendly support team. We're happy to help you every step of the way!
