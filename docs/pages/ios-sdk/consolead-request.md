---
title: Console Ad Model Request
sidebar: ios_sdk_sidebar
permalink: /consolead-request
summary: AGConsoleAdModelRequest class provides basic methods to build Console ad request URL and to request Console ad model.
---

## Make URL to Request Ad by Spot ID

```
// Make ad request URL
NSURL *url = [AGConsoleAdModelRequest makeUrlForSpotId:@"spotId" andTargetingParameters:targetingParameters];
```

Build request URL to load Console ad meta data.

## Request Ad Model

```
// Request Console ad model
[AGConsoleAdModelRequest requestAdModelWithUrl:url andCompletion:^(AGConsoleAdModel *adModel, NSError *error) {
    if (error != nil) {
        // Handle error
    }
}];
```

Asynchronous method that requests Console ad meta data from URL and builds corresponding ad model.
