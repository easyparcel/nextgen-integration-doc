# How do I import and fulfil my Magento orders by using EasyParcel in next Gen?

This guide will walk you through Orders Fulfilment NextGen EasyParcel with Magento using the **Import Version** method. With this integration, you'll import orders from Magento into your EasyParcel account for fulfilment, and the tracking number is sent back to your Magento order.

---

## Steps to import and fulfil orders using Magento Import method

#### **Step 1:** In the menu, under "Integration", click on "Installed Ecommerce Apps", find "Magento" and click on "Open App" button.
<img  alt="f01-open-app" src="https://github.com/user-attachments/assets/eb95522c-e39c-46a6-b9b9-f45e8ce7b7ff" />


#### **Step 2:** Find your connected store on the store page, and click into the store.
<img alt="f02-store-list" src="https://github.com/user-attachments/assets/554a98f8-2302-4a04-af2c-c44ce91d4491" />


#### **Step 3:** Click on "Magento Order", select the order date and order status and click on the "Search" button. The order will be imported and shown in the list below. Then, click the "Fulfill" button on the order you want to fulfill and choose **Standard Delivery**.

The status filter uses your Magento order status groups. **Processing** (paid orders waiting to ship) is selected by default.
<img alt="f03-orders" src="https://github.com/user-attachments/assets/cfd05b58-0904-4435-ae84-d62511c406f9" />



#### **Step 4:** After choosing "Standard Delivery", you can find your order details and click on the "Get Quote" button.
<img alt="f04-get-quote" src="https://github.com/user-attachments/assets/bfcdb664-ebdf-4910-ba22-94619f57b6e1" />



#### **Step 5:**  Choose the preferred courier option and click on the "Pay Now" button.
<img alt="f05-choose-courier" src="https://github.com/user-attachments/assets/db662a94-844a-4c94-96fd-6a37821ffb4a" />



#### **Step 6:** The order status, order number, shipment number, and price will be displayed. Click on the "View Orders" button.
<img alt="f06-order-placed" src="https://github.com/user-attachments/assets/2e74837e-8545-497a-a802-53156e830e67" />


#### **Step 7:**  The fulfilled order will now be displayed on the "Fulfilled Orders" tab, grouped by the batch you paid for.
<img alt="f07-fulfilled-order" src="https://github.com/user-attachments/assets/8086e695-6a9e-483a-b38e-3946ede1c4b6" />



#### **Step 8:**  Click on the "Details" button. Order details will be displayed on the page.
<img alt="f08-order-details" src="https://github.com/user-attachments/assets/9a25a7cd-b46a-4cef-9371-91f16a555587" />


#### **Step 9:**  In your Magento admin, open the order and go to **Shipments**. You will see a new shipment with the courier and tracking number, and Magento has emailed your customer its shipment email.

This happens automatically when **automatic tracking updates** is on in the store's Settings (see the setup guide, Step 6). A paid order becomes **Complete**. An order that has not been invoiced yet stays **Processing** in Magento, but its items show as shipped.
<img  alt="f09-magento-shipment" src="https://github.com/user-attachments/assets/98d05b04-2244-4f34-9a78-084d5720b17a" />


> 💡 Bundle products and products with variants (for example sizes) are shipped as one line each, just as your customer ordered them.

#### Done! You have successfully fulfill and order via Magento import.

If you have any questions or need further assistance, [check out our other articles](https://helpcentre-my.easyparcel.com/support/home) or reach out to our friendly support team. We're happy to help you every step of the way!
