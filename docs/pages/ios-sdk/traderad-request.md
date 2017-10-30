---
title: Trader Ad Model Request
sidebar: ios_sdk_sidebar
permalink: /traderad-request
summary: AGTraderAdModelRequest class provides basic methods to build Trader ad request URL and to request ad model.
---

## Make Request URL

```
NSURL *url = [AGTraderAdModelRequest makeUrlForSiteTagId:siteTagId width:width height:height];
```

Build request URL to load Trader ad meta data.

Takes **site tag id** as a `NSString`, as well as **width** and **height** of the ad as `int` in density independent pixels.

## Request Trader Ad Model

```
[AGTraderAdModelRequest requestAdModelWithUrl:url andCompletion:^(AGTraderAdModel *adModel, NSError *error) {
    if (error != nil) {
        // Handle error
    }
}];
```

Asynchronous method that requests Trader ad meta data from URL and builds corresponding ad model.