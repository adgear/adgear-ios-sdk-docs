---
title: Trader Segment API
sidebar: android_sdk_sidebar
permalink: /eventmanager-trader-segment
summary: Allows to programmatically update segment memberships in AdGear Trader.
---

## Overview

`AGTraderSegment` class allows to add Apple IFA (Identifier for Advertisers) to a particular segment, identified by segment ID and API Key.

To update a segment, you will fist need to create an instance of `AGTraderSegment` class.

For more information about Segment API see [Segments API Specs Page](https://adgear.atlassian.net/wiki/spaces/adgear/pages/69926919/S2S+Segments+API)

## Create Segment

Creates a Trader Segment API instance that can be used to update segment memberships.

```
AGTraderSegment *segment = [AGTraderSegment segment:segmentId apiKey:apiKey];
```

## Set TTL (Time to Live)

Sets the segment membership time to live, in seconds.

```
[segment setTtl:timeInSeconds];
```

## Enable XD (leverage the Cross-device graph)

Set to `YES` to leverage the Cross-device graph. Memberships will be added for all devices related to UID.

By default is `NO`

```
[segment setXd:YES];
```

## Enable Request Queuing

Updating the segment requires an HTTPS request.
If the device is offline, it is possible to add request to a queue and it will be automatically called when device becomes online.

The downside of queuing the request is that you will not have immediate confirmation if the request succeeded.

By default is `NO`

```
[segment setShouldQueue:YES];
```

## Make API Request to Add Device

After segment is configured, call `addDeviceWithCompletion` method to make the request and update the segment.
This method provides an optional completion block that will pass the status of the request as `NSNumber` and the `NSURL` used to modify the segment.

### Completion block variables

`NSNumber status` - `null` if request was queued, `true` value if request succeeded, and `false` value if request failed.

`NSURL url` - URL used to make the API request.

`NSError error` - error, if any occurred.

```
[segment addDeviceWithCompletion:^(NSNumber *status, NSURL *url, NSError *error) {
    if (error != nil) {
        // Handle error
    }
    if (status == nil) {
        // Status unknown
    }
    else if([status boolValue]) {
        // Status success
    }
    else {
        // Status failed
    }
}];
```

## Make API Request to Remove Device

After segment is configured, call `removeDeviceWithCompletion` method to make the request and update the segment.
This method provides an optional completion block that will pass the status of the request as `NSNumber` and the `NSURL` used to modify the segment.

### Completion block variables

`NSNumber status` - `null` if request was queued, `true` value if request succeeded, and `false` value if request failed.

`NSURL url` - URL used to make the API request.

`NSError error` - error, if any occurred.

```
[segment removeDeviceWithCompletion:^(NSNumber *status, NSURL *url, NSError *error) {
    if (error != nil) {
        // Handle error
    }
    if (status == nil) {
        // Status unknown
    }
    else if([status boolValue]) {
        // Status success
    }
    else {
        // Status failed
    }
}];
```

## Override Base URL

In rear occasion it might be necessary to make request to a different environment. It can be achieved by setting custom base URL.

Default base URL `https://ss.adgrx.com/api/v1/segments/`

```
[segment setBaseUrl:baseUrl];
```

## Override IFA (Identifier for Advertisers)

It is possible to override the IFA from the device with a custom value.

```
[segment setIfa:customIfa];
```

## Sample Code

```
NSString segmentId = @"12345";
NSString apiKey = @"your_api_key";
AGTraderSegment *segment = [AGTraderSegment segment:segmentId apiKey:apiKey];
[segment setTtl: 60 * 60 * 24 * 15];    // 15 days in seconds
[segment setXd:YES];                    // Leverage the Cross-device graph
[segment setShouldQueue:YES];           // Enable queuing for offline calls
[segment addDeviceWithCompletion:^(NSNumber *status, NSURL *url, NSError *error) {
    if (error != nil) {
        return;
    }
    NSString *statusString = status == nil ? @"UNKNOWN" : [status boolValue] ? @"SUCCESS" : @"FAILED";
    // Device added to the segment with status in statusString
}];
```
