---
title: Register Events
sidebar: ios_sdk_sidebar
permalink: /eventmanager-reg-events
summary: Register Events
---

## Register Event URL

```
[[AGEventManager sharedManager] registerUrl:url andPayload:nil withCompletion:^(BOOL success) {
    if (success) {
        // Event URL registered successfully
    }
}];
```

## Register Event by Name

```
[[AGEventManager sharedManager] registerEvent:@"EVENT_NAME" params:nil withCompletion:^(BOOL success) {
    if (success) {
        // Event registered successfully
    }
}];
```
