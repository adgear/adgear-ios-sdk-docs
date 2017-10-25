---
title: Overview
sidebar: ios_sdk_sidebar
permalink: /
summary: The AdGear iOS SDK provides developers with a set of UI tools to easily integrate ads from multiple ad serving platforms in their native iOS application. Ads are displayed inside a spot view that displays the ad creative, and the developer can freely position and animate the spot view as desired from within an iPhone or iPad application.
---

## Major Components

### Event Manager

Event manager is at the heart of AdGear mobile SDK and is responsible for registering/queuing “event” URLs and calling them when device is connected to the Internet. It is also responsible for making URL requests to the AdGear ad server back-ends, keeping track of the context data, and providing common functionalities to other modules.

### Console Ad

Represents an AdGear Console ad and is responsible for its management and offline caching.

### Trader Ad

Represents an AdGear Trader ad and is responsible for its management.

### Spot View

Renders various types of ads (hosted image and HTML/JavaScript/ThirdPartyTag with MRAID support).

### MRAID Web View - Dependency for AdGear SDK

Renders HTML ads with support for the [IAB MRAID 2.0](https://www.iab.com/guidelines/mobile-rich-media-ad-interface-definitions-mraid/) API.

## Operating Requirements

Minimum deployment target iOS version 8.
