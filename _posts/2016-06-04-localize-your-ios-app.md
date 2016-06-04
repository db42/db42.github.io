---
layout: post
title: There’s no reason why your iOS app shouldn’t be localization ready
---


Localization of an iOS app is one of the core requirements and could improve your app interaction in a significant manner.

I’ve encountered multiple projects where the technical team says project is not localizable and they’ll need some time to make it so. I believe there’s no reason for this excuse. With a simple process you can make sure that your app is always localization ready.

### Always use `NSlocalizedString` directive for user-facing string literals

Any user facing string literal should be enclosed in `NSLocalizedString` directive. This is perhaps the most important rule to follow. Do this and your app is always ready.

`NSLocalizedString(variable) -> NSLocalizedString(“<string>”)`

There are certain common circumstances where `NSLocalizedString` isn’t called directly on a string literal.

**Example**
```
var keys = [“Hong Kong”, “Shenzhen”, “Tokyo"]
tableCell.label.text = NSLocalizedString(keys[row])
```

->
```
var keys = [NSLocalizedString(“Hong Kong”), NSLocalizedString(“Shenzhen”), NSLocalizedString(“Tokyo”)]
tableCell.label.text = keys[row]
```

It might be somewhat tricky to do this in a more complex situation.

### Use [genstrings](http://www.manpagez.com/man/1/genstrings/) to generate translation keys

1. We’ve written a simple script that uses `genstrings` to collect all translation strings from the source code.
 
`genstrings <file-name>`

From `genstrings` man page:

```
The genstrings utility generates a .strings file(s) from the C or Objective-C (.c or .m) source code file(s) given as the argument(s).
```

This generates `.strings` files in all locale specific directories.

2. Use [twine](https://github.com/mobiata/twine) to collect these translations from all the `.strings` files into a single text file

`twine consume-string-file <output-file> Localizable.strings -a`

This collects all your translations in a nice format.
```
[Hong Kong]
	en = Hong Kong
	ko = 홍콩
	zh-Hans = 香港
	zh-Hans-HK = 香港
```



### Use `twine` to convert the text file containing strings (and translations) back to `.strings` files

Add a build step which uses `twine` to generate all the strings file in all of the locale specific directories from the text file. This way, you always interact with the text file created in [2] step.