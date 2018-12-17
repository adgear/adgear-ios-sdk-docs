---
title: Migration Guide
sidebar: ios_sdk_sidebar
permalink: /migration-guide
summary: This guide describes the changes required to migrate your application from using AdGear iOS SDK version 4 to version 5.
---

## Major differences

### Removed AdGear SDK Framework

AdGear iOS SDK v4 was using `AdGearSDK` framework as a unifying module that was responsible for loading and rendering various types of ads. In AdGear iOS SDK v5 `AdGearSDK` was removed and its responsibilities are shared among following frameworks: `AdGearConsoleAd`, `AdGearTraderAd`, `AdGearSpotView`.

### New Frameworks

#### AdGearConsoleAd

Represents an AdGear Console ad and is responsible for its management and offline caching.

#### AdGearTraderAd

Represents an AdGear Trader ad and is responsible for its management.

#### AdGearSpotView

Renders various types of ads (hosted image and HTML/JavaScript/ThirdPartyTag with MRAID support).
