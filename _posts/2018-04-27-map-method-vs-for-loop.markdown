---
layout:       post
title:        "Map vs for in vs forEach challenge in Swift ⚔️"
description:  "Comparing performance of the three instructions: 'for in', 'for' and `forEach`"
date:         2018-04-27 8:00:00 +0200
categories:   swift
image:        /assets/img/post/map-method-0.png
---

![Vision]({{ page.image }})

## How to iterate?

Probably when you want to iterate through an array of the elements, your first thought is: `for`. But there are more than one method to tackle that situation.

The most popular solutions are:
- `for in`
- `forEach()`
- `map()`

Which one is the fastest?

[This post](https://twitter.com/szubyak/status/954329152160780288) on Twitter inspired me to do the test.


## Testing the approaches

The tests include one, large array.

```swift
let arrayLength = 10_000_000

var numbers = [Int]()

for index in 1...arrayLength {
    numbers.append(index)
}
```

Each test method includes just iterating through that array using one of the previously mentioned approach. The winner is the method which will pass the test in the smallest amount of time.

```swift
func testForIn() {
    measure {
        for _ in numbers { }
    }
}

func testForEach() {
    measure {
        numbers.forEach { _ in }
    }
}

func testMap() {
    measure {
        _ = numbers.map { _ in }
    }
}
```

The complete repository can be found [here](https://github.com/albinekcom/MapVsForInVsForEachChallenge).


## Test environment

- Device: MacBook Pro (15-inch, Mid 2015, 2.2GHz Intel Core i7, 16GB RAM)
- OS: macOS High Sierra 10.13.4
- Swift: 4.1
- Array length: 10,000,000


## Test results

| Variant     | Average duration |
|-------------|------------------|
| `map()`     | 1.227 sec        |
| `for in`    | 1.892 sec        |
| `forEach()` | 2.135 sec        |

`map()` is the fastest, `forEach()` is the slowest.


## Conclusions

- `map()` is the fastest so if you really need the best performance - use it!
- `forEach()` and `for in` invoke closure on each element in the sequence in the same order, `map()` works differently and this probably impacts mostly on the performance
- Readability first, so I will prefer `for in` or `forEach()` instead of `map()` for typical situation. It is useful especially when you cooperate with many people on the same codebase to minimize questions about the code during reviewing.
