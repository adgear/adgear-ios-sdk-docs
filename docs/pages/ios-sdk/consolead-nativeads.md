---
title: Native Ads
sidebar: ios_sdk_sidebar
permalink: /consolead-nativeads
summary: It is possible to use AdGear SDK as an ad model delivery system for native ads.
---

## Overview

In order to create a native ad you will need:

1. Create a native view that will show ad data in the context of your application.

2. Create an ad in AdGear Console that will contain necessary information for the native ad to be properly displayed on the device.

3. Load ad model from AdGear Delivery

4. Provide ad data from the ad model to your custom native ad view and display it on the device.

5. Register impressions and interactions using the ad model.

## Sample Code

```
// Create your custom native ad view.
CustomNativeAdView *nativeAdView = [[CustomNativeAdView alloc] init];

// URL to load ad model from AdGear Console.
NSURL *url = [AGConsoleAdModelRequest makeUrlForSpotId:spotId andTargetingParameters:targetingParameters];

// Load ad model and and build a native ad view with the data from the model.
[AGConsoleAdModelRequest requestAdModelWithUrl:url andCompletion:^(AGConsoleAdModel *adModel, NSError *error) {
    if (error != nil) {
        // Handle error
        return;
    }

    // Set the model into the native ad view.
    [nativeAdView renderAd:adModel];

    // Display native ad...
    [self.view addSubview:nativeAdView];

    // Register impression as necessary.
    [adModel registerImpressionUrl:^(NSError *error) {
        if (error != nil) {
            // Handle error
        }
    }];
}];
```

## Sample Project

Check sample project to see native ads in action [here]({{site.baseurl}}/consolead-native-sample-project)
