# Access Control

Access control is used to restrict parts of your code from code in other files or modules. We use varying access levels to signify intention and availability of code to other developers.

**Table of Contents:**
- [Access Control](#access-control)
  - [Key Considerations](#key-considerations)
  - [Subclassing](#subclassing)
  - [Reference Docs](#reference-docs)

## Key Considerations
* Default to `private`. Anything that can be fully private should be. Use `private(set)` if you need to access externally, but only allow setting internally.
* Never explicitly use `internal`. It is the default access level, so it never needs to be specified.
* Only use `public` when a symbol needs to be used outside of its defining module.

## Subclassing
* Declare classes as `final` unless you intend for the type to be subclassed.
* Only declare classes as `open` when you intend for the type to be subclassed outside of its defining module.

## Reference Docs
* [Access Control — The Swift Programming Language](https://docs.swift.org/swift-book/LanguageGuide/AccessControl.html)
