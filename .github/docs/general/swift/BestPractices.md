# Swift Best Practices 🦅

Follow Swift's [API Design Guidelines](https://www.swift.org/documentation/api-design-guidelines/) whenever possible.

**Table of Contents:**
- [Swift Best Practices 🦅](#swift-best-practices-)
- [DateFormatters](#dateformatters)

# DateFormatters

When employing date formatters, it is advisable to provide the formatter's influencing parameters as injectable inputs, rather than injecting the entire formatter itself. This approach enhances our ability to construct effective unit tests for the corresponding code.

For instance:
```swift
SomeView(
	status: .cancelled,
	dateFormatter: .fullDateFormatter(timeZone: .utc, locale: .enUS)
)
```

If we inject the entire date formatter, our ability to truly assess the behavior would be compromised. Notably, if the actual class were to modify its formatter, the test would falsely report success.

To address this concern, it is recommended to inject the parameters that influence the formatter, such as `TimeZone` and `Locale`. By adopting this approach, any alteration to the specific formatter would be reflected accurately in the test outcome.

For more details, refer to the [UnitTesting](../testing/UnitTesting.md) document.