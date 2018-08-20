---
layout:       post
title:        "To if let or to not nil? 💀"
description:  "Comparing performance of the two instructions: 'if _ = let' and 'if something != nil'"
date:         2018-07-08 22:00:00 +0200
categories:   swift
image:        /assets/img/post/to-if-let-or-to-if-not-nil-0.png
---

![Cover]({{ page.image }})

## Is it `nil`?

You have a variable that can have a value or it can be equal `nil` (reference to nothing).

```swift
var someVariable: Int? = nil
// (...)
someVariable = 42
//(...)
```

When you want to check if something is not empty you probably think of that instruction:

```swift
if someVariable != nil {
  // do something when someVariable is not nil
}
```

In Swift there is something like optional unwrapping and this unwrapped value can be used:

```swift
if let unwrapped = someVariable {
  // do something with unwrapped variable
}
```

If you don't need that value, you can use that instruction to check if something it not `nil`:

```swift
if let _ = someVariable {
  // do something when someVariable is not nil
}
```

So now we have 2 instructions for the same thing. Which one shall we use? 🤔


## Show me the numbers

The tests include one, quite large array.

```swift
let arrayLength = 10_000_000

var numbers = [Int]()

for index in 1...arrayLength {
    numbers.append(index)
}
```

Each test method includes just iterating through that array using one of the previously mentioned approach. The winner is the method which will pass the test in the smallest amount of time.

For `if let` it is:

```swift
func testIfLet() {
    measure {
        for _ in 0..<self.attempts {
            if let _ = self.value {}
        }
    }
}
```

For `if not nil` it is:

```swift
func testIfNotNil() {
    measure {
        for _ in 0..<self.attempts {
            if self.value != nil {}
        }
    }
}
```

The complete repository can be found [here](https://github.com/albinekcom/NotNilChallenge).


## Test environment

- Device: MacBook Pro (15-inch, 2017, 2.8GHz Intel Core i7, 16GB RAM)
- OS: macOS High Sierra 10.13.3
- Swift: 4.1.2
- Array length: 10,000,000


## Test results

| Variant                   | Average duration |
|---------------------------|------------------|
| `if let _ = someVariable` | 0.165 sec        |
| `if someVariable != nil`  | 0.184 sec        |

For `Swift 4.1` `if let _ = someVariable` is about **12%** faster than `if someVariable != nil`.


## Some history

Now we know what is the fastest but is it worth to take care about 12% better performance? When we look at the older versions, you can notice that for different version of Swift language there are different results.

### Swift 3.1

| Variant                   | Average duration |
|---------------------------|------------------|
| `if let _ = someVariable` | 0.046 sec        |
| `if someVariable != nil`  | 0.754 sec        |

For `Swift 3.1` `if let _ = someVariable` is about **1539%** faster than `if someVariable != nil`.

### Swift 4.0

| Variant                   | Average duration |
|---------------------------|------------------|
| `if let _ = someVariable` | 0.193 sec        |
| `if someVariable != nil`  | 0.887 sec        |


For `Swift 4.0` `if let _ = someVariable` is about **360%** faster than `if someVariable != nil`.


## Conclusions

- `if let _ = someVariable` has better performance.
- The solution from the past could be not the best right now so be prepared for the changes.
- The performance of the some of the instructions are different using various version of the language (changes in the compiler). So when you use something because it is faster than another instruction - make sure that you are 100% right and check it when you use the newest version of your programming language. 😉


## Epilog

These results are measured using method `measure()` included in `XCTest` framework during testing (which is in `Debug` mode by default). Is it the same performance on production when the final code is optimized by the compiler? Stay tuned for the next blog post. 😉
