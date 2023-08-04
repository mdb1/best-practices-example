# Localization

## How do we use it?
We use the localization tools and APIs provided by Apple, e.g. `NSLocalizedString`.

## Localizable Keys

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

// Localizeble file:
"Greet$1" = "Hello %@";

// Result:
"Hello Manu"
```