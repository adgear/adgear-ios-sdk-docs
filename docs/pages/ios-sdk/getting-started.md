---
title: Getting Started
sidebar: ios_sdk_sidebar
permalink: /getting-started
summary: Follow this quick start and you'll be up and running in about five minutes!
---


## Create new project and import frameworks
Open Xcode and create new Single View Application project.
![Single View Application]({{site.baseurl}}/assets/images/create-project1.png)

Click Next and select name for your new project. Then click Next again.
![Name your project]({{site.baseurl}}/assets/images/create-project2.png)

In the newly created project set the Deployment Target to ```8.0``` and copy unpacked frameworks into the project.
![Set Deployment Target and copy Frameworks]({{site.baseurl}}/assets/images/create-project3.png)

Add frameworks to Embedded Binaries by clicking on "+" button in Embedded Binaries section. Then select frameworks like shown on the picture and click "Add" button.
![Add frameworks to Embedded Binaries]({{site.baseurl}}/assets/images/create-project4.png)

Your project target General Settings should look like this.
![General Settings]({{site.baseurl}}/assets/images/create-project5.png)

## Configure App Transport Security
Select `info.plist` file in your project and configuring App Transport Security Exceptions by adding the following keys.

```
<key>NSAppTransportSecurity</key>
<dict>
  <key>NSAllowsArbitraryLoads</key>
  <true/>
</dict>
```

![App Transport Security Exceptions]({{site.baseurl}}/assets/images/configure-app-transport.png)

## Modify ViewController.m file
Import AdGearSDK Module by adding the following code in the top of your `ViewController.m` file.

```
@import AdGearSDK;
```

Add AGSpotView property in the interface section and declare that the view controller implements `AGSpotViewDelegate` protocol.

```
@interface ViewController () <AGSpotViewDelegate>
@property (nonatomic, strong) AGSpotView *spotView;
@end
```

Add required delegate method.

```
- (UIViewController *)spotViewPresentingViewController {
    return self;
}
```

Modify viewDidLoad method to include the following.

```
- (void)viewDidLoad {
    [super viewDidLoad];
    
    self.spotView = [[AGSpotView alloc] initWithFrame:CGRectMake(0, 20, 336, 280)];
    self.spotView.delegate = self;
    [self.view addSubview:self.spotView];
    
    [AGAdRequest adWithSpotId:@"10746221" targetingParameters:nil andCompletion:^(AGAd * _Nullable ad, NSError * _Nullable error) {
        [self.spotView loadAd:ad];
        [self.spotView registerImpression];
    }];
}
```

At the end your `ViewController.m` file should look like this.

```
//
//  ViewController.m
//  AdGearSDK GettingStarted
//
//  Created by You on 2016-01-28.
//  Copyright © 2016 YourCompany. All rights reserved.
//

@import AdGearSDK;

#import "ViewController.h"

@interface ViewController () <AGSpotViewDelegate>
@property (nonatomic, strong) AGSpotView *spotView;
@end

@implementation ViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    
    self.spotView = [[AGSpotView alloc] initWithFrame:CGRectMake(0, 20, 336, 280)];
    self.spotView.delegate = self;
    [self.view addSubview:self.spotView];
    
    [AGAdRequest adWithSpotId:@"10746221" targetingParameters:nil andCompletion:^(AGAd * _Nullable ad, NSError * _Nullable error) {
        [self.spotView loadAd:ad];
        [self.spotView registerImpression];
    }];
}

- (void)didReceiveMemoryWarning {
    [super didReceiveMemoryWarning];
    // Dispose of any resources that can be recreated.
}

- (UIViewController *)spotViewPresentingViewController {
    return self;
}

@end
```

## Run the project
You should see an ad displayed.

![Ad displayed]({{site.baseurl}}/assets/images/run-project.png)
