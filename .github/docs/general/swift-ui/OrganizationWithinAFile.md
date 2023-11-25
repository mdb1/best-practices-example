# SwiftUI's Organization Within a File

- `properties` then `init` then `body`
- Property Wrappers grouped together
- Helper code inside an extension

## Example:

```swift
struct SettingsView: View {
    // 1. First the properties (ordered by access level).
    var someInternalProperty: Int = 15
    // Property Wrappers grouped together
    @AppStorage(AppStorageKeys.keyTwo) private var propertyTwo = 0.75
    @AppStorage(AppStorageKeys.keyThree) private var propertyThree = 0.5
    @StateObject private var object = DeviceObserver()
    
    // 2. Then the initializer.
    init(
        sliderValue: Binding<Double>, 
        wasSessionPreviouslyRunning: Binding<Bool>,
        settingsViewModel: SettingsViewModel
    ) {
        self._sliderValue = sliderValue
        self._wasSessionPreviouslyRunning = wasSessionPreviouslyRunning
        self.settingsViewModel = settingsViewModel
    }
    
    // 3. Then the body.
    var body: some View {
        List {...}
            .listStyle(.insetGrouped)
    }
}

// 4. The rest of the code in a private extension.
private extension SettingsView {
    var something: Bool {
        // Something
    }

    var object: Object {
        // get object
    }

    func doSomething() {
        // method
    }

    func summarize(_ models: [Model]) -> ModelSummary {
        // method
    }
}

/// Note: Previews should live in a different file with the `_Previews.swift` suffix.
```