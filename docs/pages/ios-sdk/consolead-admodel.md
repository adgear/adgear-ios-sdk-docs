---
title: Console Ad Model
sidebar: ios_sdk_sidebar
permalink: /consolead-admodel
summary: AGConsoleAdModel class represents Console ad model and provides basic methods to register ad impression and save the ad to local cache (to be able to serve the ad without Internet connection).
---

## Register Impression URL

```
// Register impression
[adModel registerImpressionUrl:^(NSError *error) {
    if (error != nil) {
        // Handle error
    }
}];
```

Asynchronously registers ad impression by adding impression URL to the Event Manager queue.

## Cache Ad to Local Storage

```
// Register impression
[adModel cacheAdToLocalStorage:cacheKey cacheData:customData completion:^(AGConsoleAdModel *adModel, NSError *error) {
    if (error != nil) {
        // Handle error
    }
}];
```

This method asynchronously caches ad and all the files referenced by this ad to a local storage.

It takes cache key as a `NSString` in first argument that will later be used to retrieve the ad from the cache.

You can save custom data alongside the ad by providing a `NSDictionary` as a second argument.

## Get Impression Tracker URL

```
NSURL *impressionTrackerUrl = [adModel impressionTrackerUrl];
```

## Get Click Tracker URL

```
NSURL *clickTrackerUrl = [adModel clickTrackerUrl];
```

## Get Click URL

```
NSURL *clickUrl = [adModel clickUrl:@"clickName"];
```

## Get Interaction URL

```
NSURL *interactionUrl = [adModel interactionUrl:@"interactionName"];
```

## Get File URL

```
NSURL *fileUrl = [adModel fileUrl:@"fileName"];
```

## Get Variable Value

```
NSString *value = [adModel variable:@"variableName"];
```

## Get File Keys

```
NSArray *fileKeys = [adModel fileKeys];
```
