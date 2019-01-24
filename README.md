# Install Firebase with Carthage

Here you can find an (almost official) guide in how to add Firebase with Carthage.

For information about setting up a Firebase project in the Firebase Console, please refer to [this](https://firebase.google.com/docs/ios/setup) guide.

## Adding Firebase
### Carthage Integration
1. add firebase binary frameworks to the Cartfile

```
#Firebase
binary "https://dl.google.com/dl/firebase/ios/carthage/FirebaseAnalyticsBinary.json"
binary "https://dl.google.com/dl/firebase/ios/carthage/FirebaseMessagingBinary.json"
```
2. Build dependencies: `carthage update`

### Xcode
Once built, add

- FIRAnalyticsConnector.framework
- FirebaseAnalytics.framework
- FirebaseCore.framework
- FirebaseCoreDiagnostics.framework
- FirebaseInstanceID.framework
- GoogleAppMeasurement.framework
- GoogleUtilities.framework
- nanopb.framework

to your project

Depending on which features you need to integrate, you'll need various additional frameworks. The easiest way to figure out _which_ frameworks to add is to download the [Firebase SDK](framework SDK zip) and study the `README.md` file and the folder structure.

To integrate `Messaging` for instance, you find the contents of the Messaging folder and see that you would need to add:

  - FirebaseMessaging.framework
  - Protobuf.framework

to your project...so you do that from the `Carthage/Build/iOS` folder.

Almost there :)

- Add -ObjC to "Other Linker Flags"
- Build and pray

If you start seeing weird linker errors about GoogleAnalytics something something, you may need to add `CoreData` as a dependency to your project.


Points to be aware of:
  - Remember to set the `-Obj` flag in Other Linker Flags
  - Add the following dependencies, besides from the Firebase frameworks:
    ```sh
    libc++.tbd
    libsqlite3.tbd
    Security.framework
    iAd.framework
    StoreKit.framework
    ```
  - Remember *NOT* to add the Firebase.framework in list of frameworks
  - Be aware that this way of implementing Firebase, won't necessarily guarentee you the newest versions - you need to keep your binary .json files updated, to get the newest version when running `carthage update`, and then hope that Google keeps these files up to date as well.

If in doubt of implementation, have a look at the [demoproject](https://github.com/firebase/firebase-ios-sdk) :-)
