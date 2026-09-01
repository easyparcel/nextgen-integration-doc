# Setting Up International Shipping 🌏✈️

Hi! 👋

In this documentation, we will guide you through setting up international shipping in Shopify with EasyParcel.

Ready to ship beyond borders? 🌎 Whether you are sending parcels to neighbouring countries or reaching customers worldwide, this guide will walk you through the steps to configure your Shopify store for international deliveries.

Let’s get your store ready for global shipping! 🚀

---

> ⚠️ **Important: Shopify Carrier-Calculated Shipping Requirement**
>
> Shopify requires the **Carrier-Calculated Shipping** feature to display **third-party live shipping rates** during checkout.
>
> This feature is included in:
>
> - **Shopify Advanced plan**
> - **Shopify Plus plan**
>
> For the **Shopify Grow plan**, the store must be on **annual billing** to access this feature.
>
> If you are using the **Shopify Grow plan with monthly billing**, you may either:
>
> - **Add the Carrier-Calculated Shipping feature** to your plan with an additional monthly fee, or
> - **Switch to annual billing** to enable this feature.

---

## 1. Shopify Markets Setup 🌏

Before setting up international shipping, you will need to create an international market in Shopify.

1. Go to Shopify Admin → Markets.

2. Click Create market.

<img src="https://raw.githubusercontent.com/easyparcel/nextgen-integration-doc/main/Pictures/create-market.png">

3. Enter a market name.

For example:

- International, if you want to ship to countries worldwide.
- Asia Pacific, Europe, or other regions if you want to separate your target countries by continent.

4. Select the countries or regions you want to include in this market.

5. Click Save.

<img src="https://raw.githubusercontent.com/easyparcel/nextgen-integration-doc/main/Pictures/add-market.png">

### Understanding Market Settings

Shopify will show a list of settings under the market configuration.

Some settings are marked as Inherited. This means the market will automatically use the settings from your main market.

For example:

- Currency
- Catalogs
- Discounts
- Online Store settings
- Checkout settings
- Taxes and duties

You do not need to change these settings unless you want different configurations specifically for your international customers.

For shipping setup, the important part is making sure the correct countries are included in your market. The shipping rates will be configured separately in your Shopify shipping settings.

💡 Tip: If you are only shipping to specific countries, avoid selecting all countries. Creating separate markets makes it easier to manage different shipping rates and customer experiences.

---

## 2. Configure International Shipping 🚚🌏

After creating your International Market, Shopify will prompt that shipping rates are not set up yet.

<img src="https://raw.githubusercontent.com/easyparcel/nextgen-integration-doc/main/Pictures/manage-shipping.png">

Click Manage shipping. This will redirect you to the Shipping and delivery settings page.

<img src="https://raw.githubusercontent.com/easyparcel/nextgen-integration-doc/main/Pictures/shipping-page.png">

### Add International Shipping Zone

1. Select the shipping profile that you want to add international shipping to.

<img src="https://raw.githubusercontent.com/easyparcel/nextgen-integration-doc/main/Pictures/shipping-profile.png">

2. Click Add zone.

3. Select the countries or regions that you want to ship to. Done.

4. Click Add shipping option.

<img src="https://raw.githubusercontent.com/easyparcel/nextgen-integration-doc/main/Pictures/add-zone.png">

5. Under Rate Type, select:

    Carrier or app calculated

6. Under Carrier or app, select:

    EasyParcel (via app)

7. Click Done, the shipping option will be added to your international shipping zone. 

<img src="https://raw.githubusercontent.com/easyparcel/nextgen-integration-doc/main/Pictures/shipping-option.png">

8. Click Save.

<img src="https://raw.githubusercontent.com/easyparcel/nextgen-integration-doc/main/Pictures/save-setting.png">

🎉 Your Shopify store is now connected with EasyParcel for international shipping!

---

## 3. Configure International Shipping in EasyParcel App 📦🌏

After setting up Shopify shipping rates, you will need to configure the international shipping zones and courier services in the EasyParcel app.

1. Go to EasyParcel App → Settings → Courier Setting.

2. Click Add Zone.

<img src="https://raw.githubusercontent.com/easyparcel/nextgen-integration-doc/main/Pictures/ep-courier.png">

3. Enter your Zone Name.

For example:

- Singapore
- Asia Pacific
- International

4. Click Add Destination and select the countries or regions that you want to ship to.

5. Click Save.

<img src="https://raw.githubusercontent.com/easyparcel/nextgen-integration-doc/main/Pictures/ep-addzone.png">

### Add Courier Service

After saving the zone, add the available courier services for that zone.

1. Click Add Courier Service.

2. Select your preferred courier service.

3. Click Save.

<img src="https://raw.githubusercontent.com/easyparcel/nextgen-integration-doc/main/Pictures/ep-addcourier1.png">

<img src="https://raw.githubusercontent.com/easyparcel/nextgen-integration-doc/main/Pictures/ep-addcourier2.png">

🎉 You're all set!

Your Shopify store is now ready to accept international orders with EasyParcel shipping rates.

You may now test the checkout flow on your store by entering an international delivery address and checking if the available shipping options appear correctly.