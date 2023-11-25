# Build Times

## Build with Timing Summary and Recent Build TimeLine:

Xcode provides two great tools to measure the compilation time:

### 1. Build with Timing Summary: 
From the `Product` Menu -> Perform Action -> Build With Timing Summary:
  * _Note: For clean builds, remember to clean the build folder (`Command + Shift + K`) before performing the build._
  * Once the build finishes, select it from the `Report navigator`, select `Recent` and `All Messages` sub tabs, then scroll all the way down to check the report.

### 2. Recent Build TimeLine

The `Recent Build TimeLine` feature is quite handy for analyzing build times. To access it, select a recent build and go to `Editor -> Assistant`. This timeline view provides a visual representation of build processes and times, helping us identify areas that need optimization.

## Improve Compile Time in Xcode Projects:

The first step is to make Xcode display warnings in the code that takes too long to compile:

1. Select the target project.
2. Go to the `Build Settings` tab.
3. Select the `All` sub tab.
4. Filter `Other Swift Flags`.
5. Add the following:

```bash
-Xfrontend -warn-long-function-bodies=<milliseconds>
-Xfrontend -warn-long-expression-type-checking=<milliseconds>
```

These flags enable warnings for long function bodies and expression type checking, allowing us to identify potential bottlenecks in our codebase.

## Improve Compile Time in SPM Packages:

We can actually do the same For SPM packages, by applying the following `swiftSettings` to the target:

```swift
swiftSettings: [
    .unsafeFlags([
        "-Xfrontend",
        "-warn-long-function-bodies=50",
        "-Xfrontend",
        "-warn-long-expression-type-checking=50"
    ])
]
```

## SwiftLint Rules:

The [explicit_init](https://realm.github.io/SwiftLint/explicit_init.html) and [explicit_type_interface](https://realm.github.io/SwiftLint/explicit_type_interface.html) rules can indeed help streamline our code and potentially reduce build times. Ensuring clarity in our code's initialization and type interfaces can prevent unnecessary ambiguity that might slow down the build process.

We could also add this custom rule, to avoid the usage of the `.init` sugar syntax.

```yml
  init_with_name:
    name: "Init With Name"
    message: "Prefer let object = Class() instead of let object: Class = .init()"
    included: ".*.swift"
    regex: '(?<!self|super)\.init\('
    match_kinds:
      - identifier
      - keyword
    severity: warning
```

# Additional Tips:

* Check that the scheme's build configuration is set to `Debug`.
* Avoid Type Inference: Explicitly defining types can prevent the compiler from spending extra time inferring types, leading to faster builds.
* Avoid shorthand enums usage. Instead of `status == .blocked`, use `status == UserStatus.blocked`.
* Use View Composition: Embracing view composition can result in more modular and focused code, which can lead to improved build times.
* Access Control: Employing the correct access control for our code can help the compiler optimize compilation, reducing unnecessary work.
* Use [Periphery](https://github.com/peripheryapp/periphery) to find and delete unused code.
* Watch the [Demystify parallelization in Xcode builds](https://developer.apple.com/videos/play/wwdc2022/110364/) `WWDC 2022` video.
* [BlogPost](https://www.manu.show/2023-08-18-improve-build-times-in-spm-packages-and-in-your-apps/)