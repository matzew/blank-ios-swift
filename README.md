# blank-ios-app [![Build Status](https://travis-ci.org/feedhenry-templates/blank-ios-app.png)](https://travis-ci.org/feedhenry-templates/blank-ios-app)

> Objective-C version of Blank iOS app is available [here](https://github.com/feedhenry-templates/blank-ios-app/).
> ObjC/Cocoapods of  Blank iOS app is available [here](https://github.com/feedhenry-templates/blank-ios-app/tree/cocoapods).

Author: Corinne Krych, Daniel Passos   
Level: Intermediate  
Technologies: Swift, iOS, RHMAP, CocoaPods.
Summary: A demonstration of how to get started with RHMAP.
Community Project : [Feed Henry](http://feedhenry.org)
Target Product: RHMAP  
Product Versions: RHMAP 3.7.0+   
Source: https://github.com/feedhenry-templates/blank-ios-app  
Prerequisites: fh-ios-sdk : 3.+, Xcode : 7.2+, iOS SDK : iOS7+, CocoaPods: 1.0.1+

## What is it?

Simple native iOS app to get you started with [fh-ios-sdk](https://github.com/feedhenry/fh-ios-sdk) in RHMAP. 

If you do not have access to a RHMAP instance, you can sign up for a free instance at [https://openshift.feedhenry.com/](https://openshift.feedhenry.com/).

## How do I run it?  

### RHMAP Studio

This application and its cloud services are available as a project template in RHMAP as part of the "Native iOS Blank Project" template.

### Local Clone (ideal for Open Source Development)
If you wish to contribute to this template, the following information may be helpful; otherwise, RHMAP and its build facilities are the preferred solution.

## Build instructions

1. Clone this project

2. Populate ```blank-ios-app/fhconfig.plist``` with your values as explained [here](http://docs.feedhenry.com/v3/dev_tools/sdks/ios.html#ios-configure).

3. Run ```Pod install```
> NOTE: If you clone it manually to make the app buildable in RHMAP Build farm, replace the templating ```%id%``` in ```blank-ios-app\blank-ios-app-Info.plist``` in the following block:
```xml
<key>CFBundleIdentifier</key>
<string>%id%</string>
```

3. Open blank-ios-app.xcworkspace

4. Run the project
 
## How does it work?

### FH init

In ```blank-ios-app/ViewController.m``` the synchronization loop is started.
```
override func viewDidLoad() {
    super.viewDidLoad()
    
    // FH.init using Swift FH sdk
    // trailing closure Swift syntax
    FH.init { (resp:Response, error: NSError?) -> Void in
        if let error = error {
            self.statusLabel.text = "FH init in error"
            print("Error: \(error)")
        }
        self.statusLabel.text = "FH init successful"
        print("Response: \(resp.parsedResponse)")
    }

}

```

### iOS9 and non TLS1.2 backend

If your RHMAP is depoyed without TLS1.2 support, open as source  ```blank-ios-app/blank-ios-app-Info.plist.plist``` make sure the following line are uncommented:

```
  <key>NSAppTransportSecurity</key>
  <dict>
    <key>NSAllowsArbitraryLoads</key>
    <true/>
  </dict>
```

