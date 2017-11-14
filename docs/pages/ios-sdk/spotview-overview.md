---
title: Spot View
sidebar: android_sdk_sidebar
permalink: /spotview-overview
summary: Renders various types of ads (image and HTML/JS).
---

**Major Classes**

* `AGSpotView` - Renders `AGSpotViewAd`

* `AGSpotViewAd` - Wraps ad models (`AGConsoleAdModel` and `AGTraderAdModel`) and holds payloads in preparation for the ad to be rendered.

* `AGConsoleAdFactory` - Builds `AGSpotViewAd` from `AGConsoleAdModel` and loads ad's payloads.

* `AGTraderAdFactory` - Builds `AGSpotViewAd` from `AGTraderAdModel` and loads ad's payloads.

* `AGSpotViewDelegate` - Delegate provides feedback for various ad events and actions.

## Get Started

1. Go to **[Downloads]({{site.baseurl}}/downloads)** section and download module's `aar` file.

2. Refer to **[SDK Setup]({{site.baseurl}}/sdk-setup)** section for instructions on how to add and configure the SDK in you project.
