# swift-create-xcframework-example
[swift-create-xcframework](https://github.com/unsignedapps/swift-create-xcframework) example repository

## Environment
- Xcode12.5
- [Mint](https://github.com/yonaskolb/Mint)

## Package.swift
```swift
// swift-tools-version:5.3
// The swift-tools-version declares the minimum version of Swift required to build this package.
import PackageDescription

let package = Package(
    name: "XCFrameworks",
    products: [
        // In the case of library, xcframework is created automatically
        .library(
            name: "XCFrameworks",
            targets: [ "XCFrameworks" ])
    ],
    dependencies: [
        .package(url: "https://github.com/ReactiveX/RxSwift.git", .exact("6.2.0")),
        .package(url: "https://github.com/ishkawa/APIKit.git", .exact("5.2.0"))
    ],
    // XCFrameworks is dummy target
    // if you create RxSwift.xcframework or APIKit.xcframework, you must set these libraries to depndencies
    targets: [
        .target(
            name: "XCFrameworks",
            dependencies: ["RxSwift", "RxRelay", "APIKit"])
    ]
)
```

## Usage
If you would like to get `RxSwift.xcframework`, prepare `Package.swift` like this repository and then execute the following command.

```
// using mint
$ mint run swift-create-xcframework --platform ios --output output RxSwift
```

Created `RxSwift.xcframework`
```
.
├── Package.resolved
├── Package.swift
├── README.md
├── Sources
│   └── XCFrameworks
└── output
    └── RxSwift.xcframework
```
