# EasyParcel BigCommerce Integration

---

## Introduction
This guide will walk you through integrating NextGen EasyParcel with BigCommerce. With this integration, you'll import orders from BigCommerce into your EasyParcel account for fulfillment.

---


### Integrate your BigCommerce store in EasyParcel website
**Step 1:** [Log in to your EasyParcel account](https://account.easyparcel.com/login?client_id=c575e8cd-aa46-46db-8308-e18d25bb76c6&redirect_uri=https%3A%2F%2Fapp.easyparcel.com%2Feasyaccount%2Fcallback&state=eyJjbGllbnRfaWQiOiI1M2FmYmQzMS05OGI2LTQ3ODctOWYzOC1kMDY5ZGRkN2RiM2QiLCJyZWRpcmVjdF91cmkiOiJodHRwczovL2FwcC5lYXN5cGFyY2VsLmNvbS9sb2dpbi9vYXV0aC9jYWxsYmFjayIsInN0YXRlIjoie30iLCJjb3VudHJ5IjoibXkiLCJsYW5nIjoiZW4ifQ%3D%3D&country=my)

**Step 2:** After login, click on **Add Ecommerce App** under **EasyConnect** section, find **BigCommerce** and click on **Install App**
<img alt="Screenshot 2026-03-09 at 9 05 35 PM" src="https://github.com/user-attachments/assets/9bc8b8bd-ff0d-4e72-bdef-aa46d25c2e4e" />


**Step 3:** Click **Allow Access** to authorize EasyParcel to access your BigCommerce store data
<img alt="Screenshot 2026-10-21 at 11 46 19 AM" src="https://github.com/user-attachments/assets/f29b59a1-fd82-4bdb-b871-85334d6f52d9" />


**Step 4:** Enter your store name and store url, then click **Connect**
<img alt="Screenshot 2026-10-21 at 11 40 38 AM" src="https://github.com/user-attachments/assets/f568ea0e-a130-4a4e-8cbe-5a887e79b2c1" />


**Step 5:** Key in your "API Path" and "Access Token" and click on the "Submit" button.
<img alt="Screenshot 2026-10-21 at 10 37 05 AM" src="https://github.com/user-attachments/assets/bb51bcb0-1156-43f0-9439-2391e4d80197" />
EasyParcel asks for two values. You create them in your BigCommerce control panel by adding a **store-level API account**. Nothing needs to be installed on your store.

> ℹ️ You need to be the store owner, or a staff user who is allowed to create API accounts.

  1. In your BigCommerce control panel, go to **Settings › Store-level API accounts** and click **Create API account**.
     <img  alt="Screenshot 2026-10-21 at 10 50 38 AM" src="https://github.com/user-attachments/assets/8ea89ba5-cacf-46ef-b38b-b8df6cfc5831" />
     <img  alt="Screenshot 2026-10-21 at 10 52 52 AM" src="https://github.com/user-attachments/assets/28e9513a-ee9d-4958-9402-18dad7d8047d" />


  3. For **Token type**, choose **V2/V3 API token**. Under **Name**, enter a name you will recognise, for example "EasyParcel".

     The form also shows your **API path**. You will need it in EasyParcel later. It is also saved in the text file BigCommerce downloads in step 4.
     <img alt="Screenshot 2026-10-21 at 11 00 27 AM" src="https://github.com/user-attachments/assets/d2ba6226-c55a-4da6-9d76-cc4f7d05b428" />


  3. Under **OAuth scopes**, set only these three and leave everything else as **None**:
     - **Orders**: modify
     - **Products**: read-only
     - **Information & settings**: read-only

     This lets EasyParcel read your orders and products, and add the tracking number to your order when you ship it. It cannot change your products, customers or store settings.
     <img  alt="Screenshot 2026-10-21 at 11 02 15 AM" src="https://github.com/user-attachments/assets/f2b18a29-3966-49f0-806b-9c34e09cd4bc" />
     > ⚠️ Set these carefully. BigCommerce does not let you change an API account's permissions after you save it. If one is wrong, you will need to create a new API account.

  4. Click **Save**. BigCommerce shows your API credentials in a pop-up and downloads the same details as a text file. Copy the **Access Token**.
     <img alt="Screenshot 2026-10-21 at 11 04 00 AM" src="https://github.com/user-attachments/assets/2621be9e-1c9c-4426-8ea2-c16aa5033f90" />
     > 🔒 BigCommerce shows the Access Token **only once**. Keep the downloaded text file somewhere safe and treat it like a password. If you lose it, create a new API account and use its values instead.
     
     > ℹ️ EasyParcel only needs the **API Path** and the **Access Token**. You do not need to enter the Client ID or Client Secret.
     
  5. There, you may go back to the EasyParcel portal, fill in the **API Path** and **Access Token**, and press **Submit**. Paste the API Path exactly as BigCommerce shows it. It looks like `https://api.bigcommerce.com/stores/abc123/v3/`.

     **Storefront channel ID (optional).** Only fill this in if your BigCommerce store has **more than one storefront** and you want EasyParcel to import orders from just one of them. Leave it blank to import orders from every storefront.

     - Your default storefront is always **1**.
     - For another storefront, go to **Channel Manager** in your BigCommerce control panel and open that storefront. Its channel ID is the number after `/manage/channel/` in your browser's address bar. For example, `…/manage/channel/123456/overview` means the channel ID is **123456**.
     <img  alt="Screenshot 2026-10-22 at 1 43 16 PM" src="https://github.com/user-attachments/assets/5b1fc2ac-6962-43ad-be71-8c29113665a3" />

       > ⚠️ Each storefront you connect needs its own **Store URL**, and the storefront **cannot be changed** after you connect. To import orders from another storefront later, add it as a new store with that storefront's own website address.
  
       > ⚠️ If EasyParcel shows an error instead, it tells you what to check:
       > - **"This API account is missing these permissions"**: the API account was saved without one of the three permissions above. Create a new API account with the right permissions and enter its values.
       > - **"BigCommerce did not accept this Access Token"**: check that the API Path and Access Token come from the same API account, and that the account has not been deleted.
       > - **"That API Path does not look right"** or **"No BigCommerce store was found at this API Path"**: copy the API Path again, exactly as BigCommerce shows it.
       > - **"This API account belongs to a different BigCommerce store"**: you are reconnecting a store with an API account from another store. Create the API account in the store you are reconnecting.
       > - **"The Storefront channel ID must be a whole number"**: enter only the number from the address bar, such as `123456`, or leave the field blank.
       > - **"This store is connected to storefront channel …, and that cannot be changed"**: this store already imports from one storefront. To import from a different storefront, add it as a new store with its own Store URL.
       > - **"Another BigCommerce store on your account already uses the Store URL …"**: two storefronts can't share a Store URL, or their orders would mix. Add this storefront again using its own website address.
  
       > ⚠️ Keep this API account in BigCommerce. If you delete it, your store is disconnected from EasyParcel and new orders stop coming in. To fix this, create a new API account and connect your store again with its values.


**Step 6:** You will be redirected back to the setting page, now the integration is complete
<img alt="Screenshot 2026-03-09 at 9 24 44 PM" src="https://github.com/user-attachments/assets/ddce9307-884e-4d11-a02a-a415d5eb697f" />




---

### Setup Integrated App
**Step 1:** Under **EasyConnect**, click on **Installed Ecommerce Apps**, find **BigCommerce** you may find your BigCommerce app successfully install.
<img alt="560311308-d3ca26bf-2af0-4f6f-a38d-e3bd4d5812a2" src="https://github.com/user-attachments/assets/402d4c79-76e1-43c9-a24c-877d961622eb" />


**Step 2:** In the store, click **Sender Address** and key in your sender details and click on the **Update** button.
<img alt="Screenshot 2026-01-26 at 9 52 18 PM" src="https://github.com/user-attachments/assets/7980f34e-6fa1-4073-a599-fc823753a84e" />


## Conclusion
**Done ! You have successfully setup BigCommerce app in easyparcel.** You will now can fulfill orders after importing to EasyParcel NextGen website.

You may proceed to checkout our [BigCommerce Import Fulfilment Steps](https://github.com/easyparcel/nextgen-integration-doc/blob/4f13a577cbe63107150a67d256d3b532487c73d4/Import/BigCommerce/bigcommerce_import_fulfilment.md)


