# GYB2

## Overview

I had an iOS project where a gyb file was generating 10,000s lines of code, which made it a pain to debug because XCode would freak out. So I modified Apple's [GYB](https://github.com/apple/swift/blob/master/utils/gyb.py) script to support breaking the output into multiple files.

### Input

**example.swift.gyb**

```swift
// main example.swift file 🎉
let someSwiftCodeInBaseExport: String = "Hello world from the main file!"

% # create 9 files in the directory "example"
% for i in range (1, 10):

// new gyb file file${i}.swift
// Welcome to file ${i}! 🎊
let someSwiftCodeInFile${i}: String = "Hello world from file ${i}!"

% end
```

### Outputs

**example.swift**

```swift
// main example.swift file 🎉
let someSwiftCodeInBaseExport: String = "Hello world from the main file!"
```

**example/file1.swift**

```swift
// Welcome to file 1! 🎊
let someSwiftCodeInFile1: String = "Hello world from file 1!"
```

**example/file2.swift** ... **example/file8.swift**

**example/file9.swift**

```swift
// Welcome to file 9! 🎊
let someSwiftCodeInFile9: String = "Hello world from file 9!"
```


# Tutorial Video



# Example run script for an XCode build phase

```sh
# transpile .gyb files. gyb2 is an adaption I made to create multiple swift files from one gyb
find . -name '*.gyb' |                                               \
while read file; do                                              \
    tools/gyb2 --line-directive '' -o "${file%.gyb}" "$file"; \
done
```

# My Links

* <img src="https://cdnjs.cloudflare.com/ajax/libs/webicons/2.0.0/webicons/webicon-youtube-s.png" width="15"> [My YouTube channel](https://www.youtube.com/channel/UCje9o1NPdBs0vhPp7AEgWvg)
* <img src="https://cdnjs.cloudflare.com/ajax/libs/webicons/2.0.0/webicons/webicon-youtube-s.png" width="15"> [My second YouTube channel](https://www.youtube.com/channel/UC5aSLB42ZZIDtQXrZgnS1iA)
* <img src="https://www.joehinkle.io/favicon192x192.png" width="15"> [My Website](https://www.joehinkle.io/)
* <img src="https://cdnjs.cloudflare.com/ajax/libs/webicons/2.0.0/webicons/webicon-twitter-s.png" width="15"> [My Twitter](https://twitter.com/joehink95)
* <img src="https://cdnjs.cloudflare.com/ajax/libs/webicons/2.0.0/webicons/webicon-linkedin-s.png" width="15"> [My LinkedIn](https://www.linkedin.com/in/joehinkle11/)
* <img src="https://cdnjs.cloudflare.com/ajax/libs/webicons/2.0.0/webicons/webicon-android-s.png" width="15"> [My Android Apps](https://play.google.com/store/apps/dev?id=6380399300644608862)
* <img src="https://cdnjs.cloudflare.com/ajax/libs/webicons/2.0.0/webicons/webicon-apple-s.png" width="15"> [My iOS Apps](https://apps.apple.com/us/developer/joseph-hinkle/id916334630)
* 🤓 [Hire Me](https://www.joehinkle.io/services)
