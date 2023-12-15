# Localization

We use the localization tools and APIs provided by Apple, e.g. `NSLocalizedString`.

**Table of Contents:**
- [Localization](#localization)
- [.localized vs .moduleLocalized](#localized-vs-modulelocalized)
- [Localizable Keys](#localizable-keys)
- [Code to Localize](#code-to-localize)

# .localized vs .moduleLocalized
We use .localized for strings that are defined in the app's main Localizable file.
We use .moduleLocalized for strings defined in a module's Localizable file.

# Localizable Keys

We use the following rules:

```swift
"KeyName" = "Localized string";
// %@ will be replaced with the variable provided by the caller
"KeyName$1" = "Localized string %@";
// Both %@ will be replaced with the variable provided by the caller
"KeyName$1$2" = "Localized %@ string %@";
```

Example:

```swift
var text: String {
    "Greet$1".localized(with: [user.name])
}

// Localizable file:
"Greet$1" = "Hello %@";

// Result:
"Hello Manu"
```

# Code to Localize

```swift
extension String {
    var moduleLocalized: String {
        localized(bundle: .module)
    }

    /// Returns the localized value for the given key (`self`). using the main bundle.
    var localized: String {
        localized(bundle: .main)
    }

    /// Fetches a localized String Arguments
    /// - Parameter arguments: Parameters to be added in a string.
    func moduleLocalized(with arguments: [CVarArg]) -> String {
        String(format: moduleLocalized, arguments: arguments)
    }

    /// Returns the localized value for the given key (`self`).
    func localized(bundle: Bundle) -> String {
        NSLocalizedString(self, bundle: bundle, comment: description)
    }
}
```