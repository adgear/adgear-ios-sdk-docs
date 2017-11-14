---
title: Configuration for AdGear Console
sidebar: android_sdk_sidebar
permalink: /eventmanager-consolead-config
---

## Set Mobile App ID, Key, and Environment for Console Ads

In order to get your Mobile App ID, Key, and Environment you need to login into your Console account (usually at [https://admin.adgear.com](https://admin.adgear.com)), go to **Inventory** > **Mobile Apps**, and then select (or create) a Mobile App that you want to use in your project.

```
// Set Mobile App ID - REQUIRED
[[AGEContext sharedInstance] setMobileAppId:@"YOUR_MOBILE_APP_ID"];

// Set Mobile App Chip Key - REQUIRED
[[AGEContext sharedInstance] setMobileAppChipKey:@"YOUR_MOBILE_APP_KEY"];

// Set Delivery Hostname - optional
[[AGEContext sharedInstance] setBaseUrl:[NSURL URLWithString:@"https://d.adgear.com"]];
```

Once you select a specific Mobile App, you will see your configuration information on the page.

![alt text]({{site.baseurl}}/assets/images/env-config.png "Config data")

**Default values**

 * Mobile App ID: `null`

 * Mobile App Key: `null`

 * Hostname: `https://d.adgear.com`