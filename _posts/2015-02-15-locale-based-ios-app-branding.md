---
layout: post
title: How to localize app icon, app name and launch screen on iOS
---

##App name
To localize app name, you have to localize property list value for key `CFBundleDisplayName`. 
(See [Localizing Property List Values section](https://developer.apple.com/library/ios/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) for more info).


As a result you'll have following entry in `InfoPlist.strings`:

`CFBundleDisplayName = "";`

##App icon
There are two ways to specify app icon in xcode.
* Asset catalog  

No way to localize asset catalog app icon.

* Using icon images
Quoting from the [documentation](https://developer.apple.com/library/mac/documentation/CoreFoundation/Conceptual/CFBundles/BundleTypes/BundleTypes.html)

>In addition to providing localized versions of your application’s custom resources, you can also localize your application icons and launch images by placing files with the same name in your language-specific project directories. 

If you try to localize app icon image file (icon image will be moved to language directories), app is not able to load the app icon. This should not be the expected behaviour so, this is definitely a *bug*. 

Related discussion: 
https://devforums.apple.com/message/1099478#1099478

##Launch screen
There are three ways to implement a launch screen
* Launch screen xib file (from iOS8)

XCode give an option to generate localized strings file for the launch xib. But this doesn't work. Excerpts from the [apple docs](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/LaunchImages.html).

>The launch image is static, so any text you display in it won’t be localized.

Both text and images present in the launch xib can't be localized.

* Asset catalog

There is no way to localize asset catalog launch image. 

* Launch images

Localizing launch images works. Launch images for various screen sizes and OS versions are specified by file naming convention e.g. `Default-568@2x.png` etc. Simply localize these images. 
Using launch images in iOS8 is a bit tricky, you'll need to update project information plist file `Info.plist` (More details on [Stack Overflow discussion](http://stackoverflow.com/questions/25926661/how-do-i-create-launch-images-for-iphone-6-6-plus-landscape-only-apps)).


*tldr;* There is no way to localize app icons but app name and launch screen can be localized.

