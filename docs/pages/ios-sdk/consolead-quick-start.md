---
title: Console Ads Quick Start
sidebar: ios_sdk_sidebar
permalink: /consolead-quick-start
---

Console ads are coming from AdGear’s “classical” ad delivery server <a href="https://admin.adgear.com/">https://admin.adgear.com/</a>.

## 1. Add and Configure the SDK

Refer to [SDK Setup](getting-started) section for instructions on how to add and configure the SDK in you project.

## 2. Modify ViewController.m file

### Import AdGearSDK Module

Import AdGearSDK Module by adding the following code in the top of your `ViewController.m` file.

```
@import AdGearSpotView;
```

### Add AGSpotView property

Add AGSpotView property in the interface section and declare that the view controller implements `AGSpotViewDelegate` protocol.

```
@interface ViewController () <AGSpotViewDelegate>
@property (nonatomic, strong) AGSpotView *spotView;
@end
```

### Add required delegate method

```
- (nonnull UIViewController *)spotViewPresentingViewController {
    return self;
}
```

### Modify viewDidLoad method to include the following

```
- (void)viewDidLoad {
    [super viewDidLoad];
    
    // Initialize spot view and add it as a subview
    self.spotView = [[AGSpotView alloc] initWithFrame:CGRectMake(0, 40, 326, 280)];
    self.spotView.delegate = self;
    [self.view addSubview:self.spotView];
    
    self.view.backgroundColor = UIColor.lightGrayColor;
    
    // Make/reuest ad and load it into the spot view
    [AGConsoleAdFactory makeSpotViewAdWithSpotId:@"10746221" params:nil completion:^(AGSpotViewAd *spotViewAd, NSError *error) {
        if (error != nil) {
            NSLog(@"Error: %@", error);
            return;
        }
        [self.spotView loadAd:spotViewAd];
    }];
}
```

### Summary

At the end your `ViewController.m` file should look like this.

```
#import "ViewController.h"

// Import AdGearSpotView framework
@import AdGearSpotView;

@interface ViewController () <AGSpotViewDelegate>
@property (nonatomic, strong) AGSpotView *spotView;
@end

@implementation ViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    
    // Initialize spot view and add it as a subview
    self.spotView = [[AGSpotView alloc] initWithFrame:CGRectMake(20, 60, 326, 280)];
    self.spotView.delegate = self;
    [self.view addSubview:self.spotView];
    
    self.view.backgroundColor = UIColor.lightGrayColor;
    
    // Make/reuest ad and load it into the spot view
    [AGConsoleAdFactory makeSpotViewAdWithSpotId:@"10746221" params:nil completion:^(AGSpotViewAd *spotViewAd, NSError *error) {
        if (error != nil) {
            NSLog(@"Error: %@", error);
            return;
        }
        [self.spotView loadAd:spotViewAd];
    }];
}


- (void)didReceiveMemoryWarning {
    [super didReceiveMemoryWarning];
}

- (nonnull UIViewController *)spotViewPresentingViewController {
    return self;
}

@end
```

### Run the project

You should see an ad displayed.

![Ad displayed]({{site.baseurl}}/assets/images/run-project.png)