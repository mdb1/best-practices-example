# SwiftUI Best Practices 📘

Follow Swift's [API Design Guidelines](https://www.swift.org/documentation/api-design-guidelines/) whenever possible.

**Table of Contents:**
- [SwiftUI Best Practices 📘](#swiftui-best-practices-)
- [View vs Screen vs Other suffix](#view-vs-screen-vs-other-suffix)
- [Naming Files](#naming-files)
- [Constants vs Magic Numbers](#constants-vs-magic-numbers)
  - [1. In-line value](#1-in-line-value)
  - [2. Defining Constants for Reusable Values](#2-defining-constants-for-reusable-values)
  - [3. Avoiding Redundant Constants for Existing Constants](#3-avoiding-redundant-constants-for-existing-constants)


# View vs Screen vs Other suffix

- If the file is supposed to be a full screen view (the equivalent to UIKit's ViewController), we add the `Screen` suffix.
  - Examples: `LogInScreen, WelcomeScreen, DashboardScreen, MovieDetailsScreen`.
- On the other hand, if it is supposed to be a component inside a screen, we add the `View` suffix.
  - Examples: `DecoratedCardView, ImageAndTextRowView`.
- For standard components like buttons, textFields, images, etc, we follow Apple's conventions.
  - Examples: `PrimaryButton, SecondaryTextField, ProfileImage`.

# Naming Files

For each SwiftUI file that we create we can have the following files:

1. File.swift -> The SwiftUI file.
2. File_Previews.swift -> Here we will place all the code related to the Previews.
3. File+ViewModel.swift -> If the SwiftUI file needs a view model, we create it using the `+ViewModel` suffix.

# Constants vs Magic Numbers

## 1. In-line value

If a value is used only one time in a SwiftUI file, ww can just add it in-line where it's needed. This is the easiest way to write/read/understand what the SwiftUI View is supposed to look like:

```swift
someView
    .background(Color.blue)
    .foregroundStyle(.white)
    .font(.title2)
```

## 2. Defining Constants for Reusable Values
Constants are beneficial when a value is computed or used multiple times within a file.

```swift
enum ViewConstants {
    static let foregroundColor: Color = .red
}

// ...

someView
    .foregroundStyle(ViewConstants.foregroundColor)
anotherView
    .foregroundStyle(.white)
someOtherView
    .foregroundStyle(ViewConstants.foregroundColor)
```

This approach is particularly useful for values outside of the Design System, allowing easy reuse within the file.

## 3. Avoiding Redundant Constants for Existing Constants

Avoid creating constants for values that are already defined as constants in the Design System.

```swift
enum ViewConstants {
    static let padding: CGFloat = .VPadding.large
}
```

Instead, directly use .VPadding.large where needed. The rationale is that if a change is specific to a file, it's easily locatable and modifiable. However, if the change is app-wide, modifying the existing constant suffices.