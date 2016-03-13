It's highly likely that you've encountered signing identity error in xcode during build process. The common reason for this is you don't have the private key associated with the certificate (which is being used to sign the application).


```
Failed to locate or generate matching signing assets

Xcode attempted to locate or generate matching signing assets and failed to do so because of the following issues.

Missing iOS Distribution signing identity for ... Xcode can request one for you.
```

But I came across another reason where an expired certificate was present in the keychain along with the correct one. Solution is to open 'keychain access' and delete the expired certificate from both the 'login' and 'system' tab.
