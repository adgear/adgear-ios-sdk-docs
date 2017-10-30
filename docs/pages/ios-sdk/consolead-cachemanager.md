---
title: Manage Cached Ads
sidebar: ios_sdk_sidebar
permalink: /consolead-cachemanager
summary: AGConsoleAdCacheManager class provides methods to fetch, list and delete cached ads.
---

## Fetch Cached Ad Model

```
[AGConsoleAdCacheManager fetchCachedAdModelWithCacheKey:cacheKey andCompletion:^(AGConsoleAdModel *adModel, NSError *error) {
    if (error != nil) {
        // Handle error
    }
}];
```

## Fetch Cached Ad Keys

```
[AGConsoleAdCacheManager fetchCachedAdKeys:^(NSArray *keys, NSError *error) {
    if (error != nil) {
        // Handle error
    }
}];
```

## Delete Cached Ad

```
[AGConsoleAdCacheManager deleteCachedAd:cacheKey andCompletion:^(NSError *error) {
    if (error != nil) {
        // Handle error
    }
}];
```
