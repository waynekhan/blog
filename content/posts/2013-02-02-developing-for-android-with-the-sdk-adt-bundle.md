---
title: Developing for Android with the SDK ADT bundle
date: 2013-02-02T08:59:49+00:00
---

This semester, I'm taking a course on Android development. So I'll be posting a bit more Android-related stuff as we go along. I'm developing on the [MacBook Air](http://en.wikipedia.org/wiki/MacBook_Air), so get comfy with the command line.

To get started, grab a copy of the Android SDK. The Android Development Toolkit (ADT) bundle is pretty awesome. It comes with Eclipse and the plugin all setup already: [http://developer.android.com/sdk/index.html#mac-bundle](http://developer.android.com/sdk/index.html#mac-bundle).

Unzip the `.zip`, so the full path be like: `/Users/<YOUR-HOME-DIRECTORY>/Downloads/adt-bundle-mac-x86_64/`.

Now you need to connect up your Android device (I use the [Nexus S](http://en.wikipedia.org/wiki/Nexus_S)). The ADT plugin ships with the Android Virtual Device (AVD) Manager, so you could, theoretically emulate any Android device. However this takes too long a time to boot up, it's insane not to use a real hardware device. You'll need to setup Android debugging: Settings > Developer options > On > Android debugging. There are two other useful options here: Stay awake and USB debugging notify. I keep them on, but it's not mandatory.

Now, we'll need to find out what is our device serial number. Fire up Terminal, and navigate to `/Users/<YOUR-HOME-DIRECTORY>/Downloads/adt-bundle-mac-x86_64/adt/sdk/platform-tools/`:

```text
$ ./adb devices
List of devices attached
3xxxxxxxxxxxxxxx device`
```

My device ID has been mostly redacted, the starting digit should suffice. Now you are ready to start working in Eclipse. I do this via Finder.app, and then navigating to `adt-bundle-mac-x86_64/eclipse/`. There'll be an Eclipse.app somewhere, so double-click, and wait a bit.

File > New > Android Application Project. Under Application Name and Project Name, input "Foo". Under package name, input `net.waynekhan.blog.foo` -- my FQDN with its levels reversed, plus the app name `foo`. Next we'll need to define SDK levels. The defaults are good enough:

```text
Minimum: Froyo
Target: Jelly Bean
Compile with: Jelly Bean
Theme: Holo Light with Dark Action Bar
```

Stay with me! Click Next (just use the defaults for the next few pages). You should see your newly created project `Foo` in the Project Explorer. Right-click the project, and then Run As > Android Application. The first time you do that, there'll be an option to choose either an AVD, or your hardware device. Check that, and also check "Use same device for future launches", and then go. There'll be some activity on the device, and then your new application should run. It just says `Hello World!`. Awesome, we are done at last.

And hopefully I'm real hardworking and I'll continue posting up stuff with real code in a bit.
