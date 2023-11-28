# UIScaling

We use @ScaledMetric to scale components / spacings / paddings / frames / etc.

[ScaledMetric](https://developer.apple.com/documentation/swiftui/scaledmetric) is a dynamic property that scales a numeric value.

**Table of Contents:**
- [UIScaling](#uiscaling)
  - [Usage](#usage)
    - [1. Directly in the properties](#1-directly-in-the-properties)
    - [2. As a scalar](#2-as-a-scalar)
  - [Testing using Previews](#testing-using-previews)

## Usage

### 1. Directly in the properties

```swift
@ScaledMetric private var imageSize = 100.0 

var body: some View {
    Image(systemName: "cloud.sun.bolt.fill")
        .resizable()
        .frame(width: imageSize, height: imageSize)
}
```

### 2. As a scalar

```swift
@ScaledMetric private var scale: CGFloat = 1

var body: some View {
    Image(systemName: "cloud.sun.bolt.fill")
        .resizable()
        .frame(width: 100 * scale, height: 100 * scale)
}
```

We can also use the relative parameter to match up against a specific other piece of text:

`@ScaledMetric(relativeTo: .largeTitle) private var imageSize = 100.0`

## Testing using Previews

Testing larger accessibility sizes is pretty easy using Xcode's Previews:

```swift
static var previews: some View {
    MultipleBanners() // -> This one will use default dynamic size of the phone.
    MultipleBanners() // -> This one will use `.accessibility3`.
        .dynamicTypeSize(.accessibility3)
        .previewDisplayName("Accessibility")
}
```