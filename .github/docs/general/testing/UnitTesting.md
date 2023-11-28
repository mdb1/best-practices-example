# Unit Testing Strategy 🧪

For now, we will value unit-testing over every other form of tests. We should strive to always test the business logic of the new changes while not breaking the previously coded unit tests.

In the future, we will discuss the introduction of other forms of testing (UI, Snapshot, Integration testing, etc).

**Table of Contents:**
- [Unit Testing Strategy 🧪](#unit-testing-strategy-)
- [Units related to date / currency / calendar formatting](#units-related-to-date--currency--calendar-formatting)

# Units related to date / currency / calendar formatting

To ensure consistent execution of tests associated with date, currency, and calendar formatting across both the Continuous Integration (CI) environment and local development, it is necessary to provide the appropriate timezone, locale, and calendar references.

To achieve this, a series of extensions have been implemented:

`TimeZone.utc`: This extension returns a non-optional `TimeZone` instance configured with a `secondsFromGMT` value of 0, thereby representing Coordinated Universal Time (UTC).

`Locale.enUS`: This extension returns a Locale instance with the identifier `en_US`, effectively representing the English (United States) locale.

`Calendar.utcCurrent`: This extension returns the current `Calendar` object, with the `timeZone property` set to the `utc` timezone, ensuring that the calendar operates consistently in the UTC timezone.

```swift
DateFormatter.longDateFormatter(
	locale: .enUS,
	timeZone: .utc
)
```