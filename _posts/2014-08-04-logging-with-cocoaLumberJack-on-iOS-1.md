---
layout: post
title: Complete logging solution with CocoaLumberJack for iOS applications - I
---

Client device logs can be a great asset to make your iOS app bug-free. Apart from helping you debug by seeing the console logs, ability to get client device logs should be part of your logging solution.

There are other capabilities that are expected to be present in your logging framework. For example, performance, ability to perform logging asynchronously and ability to customize each log format. If you want to read about these in detail, you should go through []().

After using a couple of third party logging libraries, I have ended up using [CocoaLumberjack]() with my own customizations. 

## Getting started - Replacement for `NSLog`
This brief guide is meant to help you quickly get started. To learn more, you should definitely check out the [documentation](https://github.com/CocoaLumberjack/CocoaLumberjack).

Using `CocoaLumberjack` in place of `NSLog` will make logging more performant, asynchronous and will open it for further customizations.

* Update Podfile
```
pod 'CocoaLumberjack'
```

* CocoaLumberjack allows you to declare `ddLogLevel` in each file to have file based loggin level. Global level loggin should be enough for most people. 
Create a `Constants.h` equivalent file to define global `ddLogLevel`

```
//
//  Constants.h

#import <CocoaLumberjack/DDLog.h>

static const int ddLogLevel = LOG_LEVEL_VERBOSE;
```

Update `<solution-name>-Prefix.pch` to import `Constants.h` in all files

* Initializing logger

Set up the logger in `applicationDidFinishLaunching`

```
[DDLog addLogger:[DDASLLogger sharedInstance]];
[DDLog addLogger:[DDTTYLogger sharedInstance]];
```

* At this point, you should be ready to replace `NSLog`. The replacements for `NSLog` in `CocoaLumberjack` are 

```
#define DDLogError(frmt, ...)
#define DDLogWarn(frmt, ...)
#define DDLogInfo(frmt, ...)
#define DDLogDebug(frmt, ...)
#define DDLogVerbose(frmt, ...)
```

`DDLog` macros have the same exact syntax as `NSLog` so, you could just find and replace `NSLog`.

