---
title: Configuration for AdGear Trader
sidebar: android_sdk_sidebar
permalink: /eventmanager-traderad-config
---

## Set Base Trader (RTB Exchange) URL

```java
// Set base RTBX URL
[[AGEContext sharedInstance] setRtbxURL:[NSURL URLWithString:@"https://rtbx.adgrx.com/impressions"]];
```

If you intend to request Trader Ads from AdGear RTB Exchange, you may need to set base RTBX URL.

**Default values**

 * Base Rtbx Url: `https://rtbx.adgrx.com/impressions`
