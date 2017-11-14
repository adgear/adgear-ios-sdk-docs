---
title: Request Data with URL Session
sidebar: android_sdk_sidebar
permalink: /eventmanager-url-connection
summary: Event Manager's AGEContext class provides a conveninece method to get a pre-configured NSURLSession that includes "User-Agent" header.
---

## Make URL Sesion

```
// Pre-configured url session
NSURLSession *urlSession = [[AGEContext sharedInstance] urlSession];
```

## Make Request with Completion Handler

```
// Usage sample
[[urlSession dataTaskWithURL:url completionHandler:^(NSData * _Nullable data, NSURLResponse * _Nullable response, NSError * _Nullable error) {
    if (error != nil) {
            // Handle error
    }
}] resume];
```