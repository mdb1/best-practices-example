# View/ViewModel 🔗

**Table of Contents:**
- [View/ViewModel 🔗](#viewviewmodel-)
  - [NameSpaces](#namespaces)
  - [Dependencies in ViewModels 💉](#dependencies-in-viewmodels-)
  - [General Guidelines](#general-guidelines)

## NameSpaces

To provide a consistent feeling across the app, we will use namespaces for the view models:

```swift
// In DashboardView+ViewModel.swift
extension DashboardView {
    @MainActor
    final class ViewModel: ObservableObject {
        // Properties/Initializers
    }
}

extension DashboardView.ViewModel {
    // Functionality
}

...

// In DashboardView.swift
@StateObject private var viewModel: ViewModel = .init()
```

## Dependencies in ViewModels 💉

- [Documentation](https://mdb1.github.io/2023-02-03-enhancing-testability-without-protocols/)

## General Guidelines

- We mark the whole class as @MainActor instead of the specific methods.
- We follow [these organization guide](./OrganizationWithinAFile.md)