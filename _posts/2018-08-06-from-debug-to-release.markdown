---
layout:       post
title:        "From debug to release 🚜"
description:  "Comparing performance of the same code in the debug and in the release mode"
date:         2018-08-06 21:00:00 +0200
categories:   swift
image:        /assets/img/post/from-debug-to-release-0.png
---

![Cover]({{ page.image }})

## Debug anyone?

In the previous blog posts ([Map vs for in vs forEach challenge in Swift ⚔️](map-method-vs-for-loop) and [To if let or to not nil? 💀](to-if-let-or-to-if-not-nil)) I have tested some methods using unit tests and function `measure()` from `XCTest` framework. But are these results also legit for the production? Let's take a look that `loop` challenge and test it using different building configurations.


## From tests to the code in debug mode

We can implement `measure()` method by ourself using code like that:

```swift
func measure(attempts: Int, measuredClosure: (() -> ())) -> ([TimeInterval], TimeInterval) {
    var durationsInSeconds = [TimeInterval]()

    for _ in 1...attempts {
        let startDate = Date()

        measuredClosure()

        durationsInSeconds.append(Date().timeIntervalSince(startDate))
    }

    let averageInSeconds = durationsInSeconds.reduce(0, +) / Double(durationsInSeconds.count)

    return (durationsInSeconds, averageInSeconds)
}
```

It takes the number of attempts and code to measure, it returns the tuple which contains all the results and the average.

Let's test `for in` approach:

```swift
var numbers = Array(1...arrayLength)

let (_, averageEmptyForIn) = measure(attempts: measureAttempts) {
    for _ in numbers {}
}

print("averageEmptyForIn: \(averageEmptyForIn)")
```

Now it is time to compile it and run.

```bash
$ swift build
$ .build/debug/Comparer

averageEmptyForIn: 1.48660808801651
```

OK. It works, we have the results now it is time to rest... but suddenly someone asks:
> "Have you checked it on production?"


## From the code in debug mode to release

Going from `debug` mode to `release` mode is simple by adding one more flag to the `swift build` command. It is time to build it and execute.

```bash
$ swift build --configuration release
$ .build/release/Comparer

averageEmptyForIn: 0
```

What? `0`? What is going on?


## Magic in the release mode

In the `release` mode, the compiler uses optimization mechanism and the final performance of the application should increased. The compilation time can be longer but the final results should be better than in the `debug` mode. The compiler noticed that this `for in loop` is empty, it is pointless to execute it at all so it skips it completely during building and the results is `0`.

To measure this kind of stuff we need to put something more robust between braces. I will use a new random mechanism `Int.random(in: 1...2)` included in `Swift 4.2`. It generates a random number from inserted range so the output should be the number `1` or `2`.

```swift
let (_, averageForInSeconds) = measure(attempts: measureAttempts) {
    for i in numbers {
        _ = i + Int.random(in: 1...2)
    }
}
```

Now this sentence can be added for every previous `loop` approaches, compiled using specific configuration and launched. The repository with the improved code can be found [here](https://github.com/albinekcom/FromDebugToReleaseComparer).


## Test environment

- Device: MacBook Pro (15-inch, 2015, 2.2GHz Intel Core i7, 16GB RAM)
- OS: macOS High Sierra 10.13.6
- Swift: 4.2 (Xcode 10 Beta 5)
- Array length: 10,000,000


## Test results

### Tests

| Variant     | Average duration |
|-------------|------------------|
| `map()`     | 5.215 sec        |
| `for in`    | 5.921 sec        |
| `forEach()` | 6.083 sec        |

### Debug mode

| Variant     | Average duration |
|-------------|------------------|
| `map()`     | 5.164 sec        |
| `for in`    | 5.908 sec        |
| `forEach()` | 5.929 sec        |

### Release mode

| Variant     | Average duration |
|-------------|------------------|
| `map()`     | 2.189 sec        |
| `for in`    | 2.187 sec        |
| `forEach()` | 2.180 sec        |


## Conclusions

- The performance of the code compiled in the `debug` mode and the results of executed `tests` are similar (both complied using the same configuration).
- In the `release` mode there is no significant impact which `loop` approach is used. The results are quite the same.
- Code compiled in the `release` mode is executed faster than in `debug` mode. It should be obvious but who knows, maybe there are some edge cases. 😉
- Tests are complied in `debug` mode by default. The results of the tests can be used as indicator but the production performance could be different.
