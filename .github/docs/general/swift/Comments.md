# Comments

Anything with access level `public` requires documentation with the exception of trivial initializers.

**Table of Contents:**
- [Comments](#comments)
  - [Key Considerations](#key-considerations)

## Key Considerations
* Use Xcode’s auto documentation in most cases (`option + command + /`).
* Document `private/internal` types if you want to add clarity, but it is not required.
* The order in which parameters appear in documentation should match the order in which they appear in the corresponding API.

```swift
/// Do something with the item.
/// - Parameter item: The `Item` selected by the user.
public func doSomething(item: Item) {
    // ...
}
```
