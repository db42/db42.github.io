---
layout: post
title: Upgrading your iOS project from Crashlytics to Fabric
---

Recently I upgraded an iOS project from using Crashlytics to Fabric. I faced a couple of errors which were easy to resolve.

1. `CrashlyticsKit` - symbol not found

2. Duplicate symbols

```
/Users/dushyant/Github/project/Pods/Fabric/Crashlytics.framework/Crashlytics(CLSIcon.o)
/Users/dushyant/Github/project/Pods/Fabric/Fabric.framework/Fabric(CLSIcon.o)
duplicate symbol _OBJC_METACLASS_$_CLSIcon in:
/Users/dushyant/Github/project/Pods/Fabric/Crashlytics.framework/Crashlytics(CLSIcon.o)
/Users/dushyant/Github/ptoject/Pods/Fabric/Fabric.framework/Fabric(CLSIcon.o)
ld: 309 duplicate symbols for architecture x86_64
clang: error: linker command failed with exit code 1 (use -v to see invocation)
```

Earlier, crashlytics required one framework - `Crashlytics.framwork`. Fabric requires two frameworks - `Fabric.framework` and `Crashlytics.framework`. Note that both use different `Crashlytics.framework`.

Reason for these errors is your project is still using old `Crashlytics.framework`. You just have to delete your older `Crashlytics.framework` and let Fabric download the newer one. 

To see if your `Crashlytics.framework` is not updated, you can use `nm` which is a nifty command-line tool to see symbols in a binary. 
`nm Old-Crashlytics.framework` will reveal same symbols present in `Fabric.framework` and `CrashlyticsKits` symbol will be missing in the list.

