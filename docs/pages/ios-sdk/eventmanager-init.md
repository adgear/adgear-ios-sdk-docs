---
title: Event Manager Context
sidebar: ios_sdk_sidebar
permalink: /eventmanager-context
summary: Event Manager initialization, configuration and useful methods.
---

## Initialize Context

AGEContext class is a singleton that keeps application wide state and configuration of the SDK and is responsible for acquiring information about Identifier for Advertiser (IFA) and device’s User-Agent.

```
[AGEContext sharedInstance];
```

Event Manager Context `AGEContext` **must** be initialized when application starts, before calling any other method of the SDK.


## Set Publisher ID and Key

```
[[AGEContext sharedInstance] setPublisherId:@"YOUR_PUBLISHER_ID"];
[[AGEContext sharedInstance] setPublisherKey:@"YOUR_PUBLISHER_KEY"];
```

## Set Base URL

```
[[AGEContext sharedInstance] setBaseUrl:[NSURL URLWithString:@"https://d.adgear.com"]];
```

## Get IFA (Identifier For Advertisers)

```
NSString *ifa = [[AGEContext sharedInstance] iosId];
```

## Get IFA optout flag

```
BOOL ifaOptout = [[AGEContext sharedInstance] optout];
```

## Get User Agent

```
NSString *userAgent = [[AGEContext sharedInstance] userAgent];
```
