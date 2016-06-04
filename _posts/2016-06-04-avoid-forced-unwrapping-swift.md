---
layout: post
title: Why and how to always avoid forced unwrapping in Swift
		 ---  
  

`Optionals` is such a nice feature in Swift which is ruined by the developer’s bad practice of using forced unwrapping (`!`) irresponsibly.

Forced unwrapping (`!`) *can* cause a runtime crash because of it being `nil`. Going by the murphy’s law, it *will* cause a run time crash.

Therefore, it makes sense to not use forced unwrapping and rely on swift’s compiler magic to avoid any runtime crash related to a variable being `nil`.

You’ll notice how easy and rewarding it is to avoid forced unwrapping using [`optional-chaining`](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/OptionalChaining.html) and conditional unwrapping.

**Tip**
Use `dequeueReusableCellWithIdentifier:forIndexPath -> UITableViewCell` instead of `dequeueReusableCellWithIdentifier: -> UITableViewCell?`

### How do you force yourself and your team to adopt this practice?

 **Make Xcode warn you when you use force unwrapping**
 
 1. Install [SwiftLint](https://github.com/realm/SwiftLint).
 2. Create a `.swiftlint.yml` in your project directory. This config file tells swiftlint to generate a warning for force casting.
```
whitelist_rules:
  - force_cast
force_cast: warning # implicitly
```
 3. Add a build phase to get these warnings in the Xcode  
```
if which swiftlint >/dev/null; then
  swiftlint
else
  echo "warning: SwiftLint not installed, download from https://github.com/realm/SwiftLint"
fi
```

Happy *swifting*!


