---
title: Spot View Methods
sidebar: android_sdk_sidebar
permalink: /spotview-methods
---

## Create Spot View

`AGSpotView` class is the main rendering view for the ads. It can render ad from AdGear Console and Trader and they can be of `HTML`, `JS`, `Third Party`, or `Image` types.

```
// Create new spot view
AGSpotView *spotView = [[AGSpotView alloc] initWithFrame:CGRectMake(x, y, width, height)];
```

## Make Spot View Ad from Console Ad Model

`AGConsoleAdFactory` class provides a static asynchronous method to build a spot view ad and load its dependencies for console ad models.

```
[AGConsoleAdFactory makeSpotViewAdWithConsoleAdModel:agConsoleAdModel completion:^(AGSpotViewAd *spotViewAd, NSError *error) {
    // spotViewAd ...
}];
```

## Make Spot View Ad from Trader Ad Model

`AGTraderAdFactory` class provides a static asynchronous method to build a spot view ad and load its dependencies for trader ad models.

```
[AGConsoleAdFactory makeSpotViewAdWithTraderAdModel:agTraderAdModel completion:^(AGSpotViewAd *spotViewAd, NSError *error) {
    // spotViewAd ...
}];
```

## Set Spot View Delegate

```
[spotView setDelegate:self];
```

## Spot View Delegate Methods

```
@protocol AGSpotViewDelegate <NSObject>

@required

- (nonnull UIViewController*)spotViewPresentingViewController;

@optional

// Spot view loaded
- (void)spotViewWillLoad:(nonnull AGSpotView *)spotView;
- (void)spotViewDidLoad:(nonnull AGSpotView *)spotView;
- (void)spotViewFailedToLoad:(nonnull AGSpotView *)spotView;

// Register impression
- (void)spotViewDidCallRegisterImpression:(nonnull AGSpotView *)spotView;
- (void)spotViewFailedToCallRegregisterImpression:(nonnull AGSpotView *)spotView;

// Register event
- (void)spotView:(nonnull AGSpotView *)spotView didCallRegisterEventWithName:(nullable NSString *)name andUrl:(nullable NSURL *)url;
- (void)spotView:(nonnull AGSpotView *)spotView failedToRegisterEventWithName:(nullable NSString *)name andUrl:(nullable NSURL *)url;

// Load URL
- (BOOL)spotView:(nonnull AGSpotView *)spotView shouldOpen:(nullable NSURL *)url navigationAction:(nullable WKNavigationAction *)navigationAction;
- (void)spotView:(nonnull AGSpotView *)spotView willOpen:(nullable NSURL *)url navigationAction:(nullable WKNavigationAction *)navigationAction;
- (void)spotView:(nonnull AGSpotView *)spotView didOpen:(nullable NSURL *)url navigationAction:(nullable WKNavigationAction *)navigationAction;
- (void)spotView:(nonnull AGSpotView *)spotView failedToOpen:(nullable NSURL *)url navigationAction:(nullable WKNavigationAction *)navigationAction;

// Open
- (BOOL)mraidView:(nonnull AGMraidView *)mraidView shouldOpen:(nullable NSURL *)url navigationAction:(nullable WKNavigationAction *)navigationAction;
- (void)mraidView:(nonnull AGMraidView *)mraidView willOpen:(nullable NSURL *)url navigationAction:(nullable WKNavigationAction *)navigationAction;
- (void)mraidView:(nonnull AGMraidView *)mraidView didOpen:(nullable NSURL *)url navigationAction:(nullable WKNavigationAction *)navigationAction;
- (void)mraidView:(nonnull AGMraidView *)mraidView failedToOpen:(nullable NSURL *)url navigationAction:(nullable WKNavigationAction *)navigationAction;

// Expand
- (BOOL)mraidView:(nonnull AGMraidView *)mraidView shouldExpandFromRect:(CGRect)fromRect toRect:(CGRect)toRect;
- (void)mraidView:(nonnull AGMraidView *)mraidView willExpandFromRect:(CGRect)fromRect toRect:(CGRect)toRect;
- (void)mraidView:(nonnull AGMraidView *)mraidView didExpandFromRect:(CGRect)fromRect toRect:(CGRect)toRect;

// Resize
- (BOOL)mraidView:(nonnull AGMraidView *)mraidView shouldResizeFromRect:(CGRect)fromRect toRect:(CGRect)toRect;
- (void)mraidView:(nonnull AGMraidView *)mraidView willResizeFromRect:(CGRect)fromRect toRect:(CGRect)toRect;
- (void)mraidView:(nonnull AGMraidView *)mraidView didResizeFromRect:(CGRect)fromRect toRect:(CGRect)toRect;

// Collapse
- (BOOL)mraidView:(nonnull AGMraidView *)mraidView shouldCollapseFromRect:(CGRect)fromRect toRect:(CGRect)toRect;
- (void)mraidView:(nonnull AGMraidView *)mraidView willCollapseFromRect:(CGRect)fromRect toRect:(CGRect)toRect;
- (void)mraidView:(nonnull AGMraidView *)mraidView didCollapseFromRect:(CGRect)fromRect toRect:(CGRect)toRect;

// Hide
- (BOOL)mraidViewShouldHide:(nonnull AGMraidView *)mraidView;
- (void)mraidViewWillHide:(nonnull AGMraidView *)mraidView;
- (void)mraidViewDidHide:(nonnull AGMraidView *)mraidView;

// Play video/audio
- (BOOL)mraidView:(nonnull AGMraidView *)mraidView shouldPlayVideoURL:(nullable NSURL *)url;
- (void)mraidView:(nonnull AGMraidView *)mraidView willPlayVideoURL:(nullable NSURL *)url;
- (void)mraidView:(nonnull AGMraidView *)mraidView didPlayVideoURL:(nullable NSURL *)url;
- (void)mraidView:(nonnull AGMraidView *)mraidView failedToPlayVideoURL:(nullable NSURL *)url;

// Store picture
- (BOOL)mraidView:(nonnull AGMraidView *)mraidView shouldStorePictureWithURL:(nullable NSURL *)url;
- (void)mraidView:(nonnull AGMraidView *)mraidView willStorePictureWithURL:(nullable NSURL *)url;
- (void)mraidView:(nonnull AGMraidView *)mraidView didStorePictureWithURL:(nullable NSURL *)url;
- (void)mraidView:(nonnull AGMraidView *)mraidView failedToStorePictureWithURL:(nullable NSURL *)url;
- (void)mraidView:(nonnull AGMraidView *)mraidView refusedToStorePictureWithURL:(nullable NSURL *)url;

// Create calendar event
- (BOOL)mraidView:(nonnull AGMraidView *)mraidView shouldCreateCalendarEvent:(nullable NSString *)event;
- (void)mraidView:(nonnull AGMraidView *)mraidView willCreateCalendarEvent:(nullable NSString *)event;
- (void)mraidView:(nonnull AGMraidView *)mraidView didCreateCalendarEvent:(nullable NSString *)event;
- (void)mraidView:(nonnull AGMraidView *)mraidView failedToCreateCalendarEvent:(nullable NSString *)event;
- (void)mraidView:(nonnull AGMraidView *)mraidView refusedToCreateCalendarEvent:(nullable NSString *)event;

// Activate sensor
- (BOOL)mraidView:(nonnull AGMraidView *)mraidView shouldActivateSensor:(nullable NSString *)sensor;
- (void)mraidView:(nonnull AGMraidView *)mraidView willActivateSensor:(nullable NSString *)sensor;
- (void)mraidView:(nonnull AGMraidView *)mraidView didActivateSensor:(nullable NSString *)sensor;
- (void)mraidView:(nonnull AGMraidView *)mraidView failedToActivateSensor:(nullable NSString *)sensor;
- (void)mraidView:(nonnull AGMraidView *)mraidView refusedToActivateSensor:(nullable NSString *)sensor;
- (void)mraidView:(nonnull AGMraidView *)mraidView willDeactivateSensor:(nullable NSString *)sensor;
- (void)mraidView:(nonnull AGMraidView *)mraidView didDeactivateSensor:(nullable NSString *)sensor;

// State change
- (void)mraidView:(nonnull AGMraidView *)mraidView didChangeState:(nullable NSString *)state;

// Ready
- (void)mraidViewDidCallReady:(nonnull AGMraidView *)mraidView;

// Viewable change
- (void)mraidView:(nonnull AGMraidView *)mraidView didChangeViewable:(BOOL)viewable;

// Handling webview crashes
- (void)mraidViewContentProcessDidTerminate:(nonnull AGMraidView *)mraidView;
```

Set listener to receive various view related events.

## Display Spot View Ad

```
// Render spotViewAd in spotView
[spotView loadAd:spotViewAd];
```

Once Spot View is configured and you have your Spot View Ad ready, you can pass it to Spot View in `loadAd` method. This will render the ad on the screen.
