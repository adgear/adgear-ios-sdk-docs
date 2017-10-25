---
title: Request Ad Models
sidebar: ios_sdk_sidebar
permalink: /sdk-request-ads
summary: AGAdRequest class provides basic methods to request ad models from various sources as well as to save ads into local cache.
---

## Request Ad

### Requests Ad with Spot ID

```
[AGAdRequest adWithSpotId:spotId targetingParameters:nil andCompletion:^(AGAd * _Nullable ad, NSError * _Nullable error) {
    if (error) {
        // Handle error
    }
}];
```

### Request Ad with URL

```
[AGAdRequest adWithURL:url andCompletion:^(AGAd * _Nullable ad, NSError * _Nullable error) {
    if (error) {
        // Handle error
    }
}];
```

## Make Ad from Existing Data

### Make Ad with JSON String

```
[AGAdRequest adWithJsonString:jsonString andCompletion:^(AGAd * _Nullable ad, NSError * _Nullable error) {
    if (error) {
        // Handle error
    }
}];
```

### Make Ad with JSON Data

```
[AGAdRequest adWithData:data andCompletion:^(AGAd * _Nullable ad, NSError * _Nullable error) {
    if (error) {
        // Handle error
    }
}];
```

## Load Ad from Local Cache

### Request Ad from Local Cache with Ad URL

```
[AGAdRequest adWithCachedURL:url andCompletion:^(AGAd * _Nullable ad, NSError * _Nullable error) {
    if (error) {
        // Handle error
    }
}];
```

### Request Ad from Local Cache with Ad Cache Key

```
[AGAdRequest adWithCachedKey:cacheKey andCompletion:^(AGAd * _Nullable ad, NSError * _Nullable error) {
    if (error) {
        // Handle error
    }
}];
```

## Cache Ad Methods

### Cache Ad with URL

```
[AGAdRequest cacheAdWithURL:url andCompletion:^(NSString * _Nullable key, NSError * _Nullable error) {
    if (error) {
        // Handle error
    }
}];
```

### Get Keys for Cached Ads

```
[AGAdRequest keysForCachedAdsWithCompletion:^(NSArray * _Nullable keys) {
    // Handle keys
}];
```

### Delete Ad from Cache

```
[AGAdRequest deleteCachedAdWithKey:cacheKey andCompletion:^(NSError * _Nullable error) {
    if (error) {
        // Handle error
    }
}];
```
