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

You should see a new project window looking similar to this.

![Name your project]({{site.baseurl}}/assets/images/create-project3.png)

Download AdGear iOS SDK frameworks as "All Frameworks" zipped file from the [Downloads](downloads) page and unpack them to a temporary folder on your computer.

![Name your project]({{site.baseurl}}/assets/images/create-project5.png)

Select all frameworks and drag them into your project. You will see a diolog like the one bellow. Make sure you check "Copy items is needed".

![Name your project]({{site.baseurl}}/assets/images/create-project6.png)

Click on "Finish" button and your project should look like this.

![Name your project]({{site.baseurl}}/assets/images/create-project7.png)

Add frameworks to "Linked Frameworks and Libraries" section by clicking on "+" button in Embedded Binaries section. Then select frameworks like shown on the picture and click "Add" button.

![Add frameworks to Embedded Binaries]({{site.baseurl}}/assets/images/create-project8.png)

After clicking on "Add" button and your project should look like this.

![Name your project]({{site.baseurl}}/assets/images/create-project9.png)

## Modify ViewController.m file
Import AdGearSDK Module by adding the following code in the top of your `ViewController.m` file.

```
@import AdGearSpotView;
```

Add AGSpotView property in the interface section and declare that the view controller implements `AGSpotViewDelegate` protocol.

```
@interface ViewController () <AGSpotViewDelegate>
@property (nonatomic, strong) AGSpotView *spotView;
@end
```

Add required delegate method.

```
- (nonnull UIViewController *)spotViewPresentingViewController {
    return self;
}
```

Modify viewDidLoad method to include the following.

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

## Run the project
You should see an ad displayed.

![Ad displayed]({{site.baseurl}}/assets/images/run-project.png)
