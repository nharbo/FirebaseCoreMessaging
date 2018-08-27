# Firebase with Carthage

Here you can find an [(almost official) guide] in how to add Firebase with Carthage.

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
  - Be aware that this way of implementing Firebase, won't nessasarily give you the newest versions - you need to keep your binary .json files updated, to get the newest version when running `carthage update`, and then hope that Google keeps these files up to date as well.
 
If in doubt of implementation, have a look at the demoproject :-)


[//]: # 
   [(almost official) guide]: <https://github.com/firebase/firebase-ios-sdk/blob/master/Carthage.md>
