---
layout: post
title: Export watchkit archive to ad hoc ipa using xcode
---


After adding watchkit support to an existing iOS project, I got the following error

```
2016-03-10 11:08:30 +0000 [MT] Presenting: Error Domain=IDEFoundationErrorDomain Code=1 "ipatool failed with an exception: #<Errno::EEXIST: File exists - /var/folders/vp/pxpbzs3n45xcy51nbtjg88pc0000gn/T/ipatool20160310-39068-v2snb4/MachOs/watchos/armv7k/(dylibs)/libswiftCore.dylib>
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:93:in `initialize'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:93:in `open'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:93:in `createExclusive'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1455:in `block (2 levels) in CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1445:in `each'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1445:in `block in CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1440:in `each'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1440:in `CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1500:in `block in CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1499:in `each'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1499:in `CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1500:in `block in CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1499:in `each'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1499:in `CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1687:in `ProcessIPA'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:2210:in `<main>'" UserInfo=0x7fec7d4307f0 {NSLocalizedDescription=ipatool failed with an exception: #<Errno::EEXIST: File exists - /var/folders/vp/pxpbzs3n45xcy51nbtjg88pc0000gn/T/ipatool20160310-39068-v2snb4/MachOs/watchos/armv7k/(dylibs)/libswiftCore.dylib>
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:93:in `initialize'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:93:in `open'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:93:in `createExclusive'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1455:in `block (2 levels) in CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1445:in `each'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1445:in `block in CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1440:in `each'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1440:in `CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1500:in `block in CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1499:in `each'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1499:in `CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1500:in `block in CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1499:in `each'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1499:in `CompileOrStripBitcodeInBundle'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:1687:in `ProcessIPA'
    /Applications/Xcode.app/Contents/Developer/usr/bin/ipatool:2210:in `<main>'}
    ```

Solution:

Go to 'Build Settings' for 'Watchkitapp' and 'Watchkitapp Extension' targets and set `EMBEDDED_CONTENT_CONTAINS_SWIFT = NO;`.

Now you can archive your iOS app including watchkit.