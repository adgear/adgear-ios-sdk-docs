---
title: Render Ad and Spot View
sidebar: ios_sdk_sidebar
permalink: /sdk-spotview
summary: Renders various types of ads (image and HTML/JS).
---

## Create Spot View

AGSpotView class is the main rendering view for the ads. It can render ad from AdGear Console and Trader and they can be of HTML, JS, Third Party, or Image types.

```
AGSpotView *spotView = [[AGSpotView alloc] init];
```

## Load Ad

```
[spotView loadAd:ad];
```

## Spot View Delegate

Extend your controller class with AGSpotViewDelegate interface.

```
@interface DetailViewController () <AGSpotViewDelegate>
```

Assign your controller as a delegate for a spot view.

```
spotView.delegate = self;
```

Implement delegate methods

```
- (void)spotViewDidLoad:(nonnull AGSpotView *)spotView {
    // Spot View Did Load
}
```

```
- (void)spotViewFailedToLoad:(nonnull AGSpotView *)spotView {
    // Spot View Failed To Load
}
```

```
- (void)mraidViewDidHide:(nonnull AGMraidView *)mraidView {
    // Mraid View Did Hide
}
```

```
- (void)spotViewDidCallRegisterImpression:(nonnull AGSpotView *)spotView {
    // Spot View Did Call Register Impression
}
```

```
- (void)spotViewFailedToCallRegregisterImpression:(nonnull AGSpotView *)spotView {
    // Spot View Failed To Call Register Impression
}
```

```
- (BOOL)spotView:(nonnull AGSpotView *)spotView shouldOpen:(nullable NSURL *)url navigationAction:(nullable WKNavigationAction *)navigationAction {
    // Should Open URL
    return YES;
}
```

```
- (void)spotView:(nonnull AGSpotView *)spotView willOpen:(nullable NSURL *)url navigationAction:(nullable WKNavigationAction *)navigationAction {
    // Will Open URL
}
```

```
- (void)spotView:(nonnull AGSpotView *)spotView didOpen:(nullable NSURL *)url navigationAction:(nullable WKNavigationAction *)navigationAction {
    // Did Open URL
}
```

```
- (void)spotView:(nonnull AGSpotView *)spotView failedToOpen:(nullable NSURL *)url navigationAction:(nullable WKNavigationAction *)navigationAction {
    // Failed to Open URL
}
```

```
- (void)spotView:(nonnull AGSpotView *)spotView didCallRegisterEventWithName:(nullable NSString *)name andUrl:(nullable NSURL *)url {
    // Did Call Register Event With Name and URL
}
```

```
- (void)spotView:(nonnull AGSpotView *)spotView failedToRegisterEventWithName:(nullable NSString *)name andUrl:(nullable NSURL *)url {
    // Failed to Register Event With Name and URL
}
```
