---
title: Configure Context and Environment
sidebar: ios_sdk_sidebar
permalink: /context-and-env
summary: AdGear iOS SDK v4 has a notion of application wide context that needs to be configured depending on the intended use of the SDK.
---

## Required configuration

Every application that intends to use AdGear iOS SDK needs to specify **Mobile App ID** and **Mobile App Chip Key** values and the SDK's context prior to requesting and displaying any ads.

We recommend to configure the SDK's context in your `AppDelegate` class in `application:didFinishLaunchingWithOptions:` method.

For example, your `AppDelegate.m` should look similar to this

```objective-c
#import "AppDelegate.h"

@import AdGearSDK;

@interface AppDelegate ()
@end

@implementation AppDelegate

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    AGContext *context = [AGContext sharedInstance];
    context.mobileAppId = @"YOUR_MOBILE_APP_ID";
    context.mobileAppChipKey = @"YOUR_MOBILE_APP_CHIP_KEY";
    return YES;
}

...

@end
```

### Finding your Mobile App ID and Mobile App Chip Key values

In order to find the values you will need:

1. Log in to AdGear Console here: http://admin.adgear.com
2. Navigate to **Inventory** tab
3. Select **Mobile Apps** for type of inventory
4. Select one of your mobile applications in the list, or create a new one.
![Mobile App ID and Mobile App Chip Key]({{site.baseurl}}/assets/images/mobile-app-id-and-chip-key.png)

## Optional configuration

Beside setting **Mobile App ID** and **Mobile App Chip Key** values you could also specify (if needed) **schema**, **host**, and **port** to your ad delivery environment.

```objective-c
AGContext *context = [AGContext sharedInstance];

context.schema = @"https"; // OPTIONAL e.g. http or https
context.host = @"d.adgear.com"; // OPTIONAL
context.port = @"YOUR_CUSTOM_PORT"; // OPTIONAL e.g. 80 or 443

context.mobileAppId = @"YOUR_MOBILE_APP_ID"; // REQUIRED
context.mobileAppChipKey = @"YOUR_MOBILE_APP_CHIP_KEY"; // REQUIRED
```
