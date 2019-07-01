---
layout:       post
title:        "Start learning SwiftUI 🦆"
description:  "The easiest way to try SwiftUI, even on macOS Mojave"
date:         2019-07-01 18:00:00 +0200
categories:   swift
image:        /assets/img/post/start-learning-swiftui-0.png
---

![Cover]({{ page.image }})

## SwiftUI

Apple presented `SwiftUI` at WWDC 2019.

> SwiftUI is an innovative, exceptionally simple way to build user interfaces across all Apple platforms with the power of Swift. Build user interfaces for any Apple device using just one set of tools and APIs.

Source: [Xcode - SwiftUI - Apple Developer](https://developer.apple.com/xcode/swiftui/)

It is a new approach for coding user interface elements in applications. So... how we can start using it?

## Needed tools

The most important thing is to download the latest beta version of `Xcode 11` which can be found on [Using Apple Beta Software](https://developer.apple.com/support/beta-software/) website.

If you would like to code your project with live preview, you need to have installed `macOS Catalina` (which is in beta right now) on your computer... but there is a workaround described below to have a "look-and-feel" of live preview of coded view using still stable `macOS Mojave`.

In my opinion the biggest disadvantage of `SwiftUI` is to have an awareness that it works only on new version of operating systems (like `iOS 13, macOS Catalina, watchOS 6` etc.) so if you have a big production app with massive number of users, probably you will start using this framework in 2 years... 😱

## Playground as a sandbox

Open installed `Xcode-beta 11`, choose `File -> New -> Playground` and replace the code with these lines:

```swift
import PlaygroundSupport
import SwiftUI

struct ContentView: View {

    var body: some View {
        Text("Hello, SwiftUI!")
    }

}

PlaygroundPage.current.liveView = UIHostingController(rootView: ContentView())
```

Make any change in computed property `body` and admire "quickly refreshed" the results on the screen.

![SwiftUI in Xcode Playground](/assets/img/post/start-learning-swiftui-1.png)

## Learning resources

Despite the fact it is still in the beta phase, there are some places where you can gain more knowledge and try examples:
- [SwiftUI videos at WWDC 2019](https://developer.apple.com/videos/wwdc2019/?q=swiftui)
- [SwiftUI Tutorials - Apple Developer Documentation](https://developer.apple.com/tutorials/swiftui/)
- Tutorials from other bloggers like [SwiftUI by example](https://www.hackingwithswift.com/quick-start/swiftui)

And many many more, just use your favorite search engine to find.

## Conclusions

- Remember that `SwiftUI` is a new approach which is still in beta phase
- Install `Xcode-beta 11` next to your stable version and play with it
- Use a playground for fast prototyping until you have `macOS Catalina` installed on your computer
