## Install

### With [Cocoapods](http://cocoapods.org/)

*NOTE:* The installation via Cocoapods may currently not work due to an incompatiability with C++
libraries and Cocoapods. This is being resolved, but in the meantime installation via the
downloadable Framework below should be the way forward.

In your Podfile:

    pod "Rollbar", "~> 1.0.0-alpha"

Make sure to declare your platform as `ios` at the top of your Podfile. E.g:

    platform :ios, '7.0'

Be sure to remember to `pod install` after changing your Podfile!

### Without Cocoapods

1. Download the [Rollbar framework](https://github.com/rollbar/rollbar-ios/releases/download/v1.0.0-alpha6/Rollbar.zip).

2. Extract the Rollbar directory in the zip file to your Xcode project directory.

3. In Xcode, select _File_ -> _Add Files to "[your project name]"_ and choose the Rollbar directory from step 2.

   Note: if step three doesn't work you can also extract the Rollbar directory anywhere, and drag the `.framework` files into XCode, allowing XCode to correctly configure the Frameworks.

4. Add the libc++ library to your link binary with libraries build phase

5. Ensure that `-ObjC` is in your "Other Linker Flags" setting. Note that the `-all_load` flag is
   not recommended but would also work for this purpose if you already have that set.

## Setup

In your Application delegate implementation file, add the following import statement:

```objc
#import <Rollbar/Rollbar.h>
```

Then add the following to `application:didFinishLaunchingWithOptions:`:

```objc
[Rollbar initWithAccessToken:@"POST_CLIENT_ITEM_ACCESS_TOKEN"];
```

<!-- RemoveNext -->
Replace `POST_CLIENT_ITEM_ACCESS_TOKEN` with a client scope access token from your project in Rollbar

That's all you need to do to report crashes to Rollbar. To get symbolicated stack traces, follow the instructions in the "Symbolication" section below.
