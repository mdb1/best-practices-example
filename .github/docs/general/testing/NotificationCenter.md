# Testing NotificationCenter: Concurrency vs Threading

## Synchronous Code

When we want to add unit tests to the NotificationCenter, and the code we want to test runs on a synchronous way:

```swift
center.publisher(for: .someNotification)
    .sink { [weak self] _ in
        self?.number += 1 // -> This is what we want to test
    }
    .store(in: &subscribers)
```

We can just test it synchronously:

```swift
func test_viewModel_subscriber() {
    // Given
    XCTAssertEqual(sut.number, 0)
    // When
    center.post(name: .someNotification)
    // Then
    XCTAssertEqual(sut.number, 1) // Synchronous code
}
```

## Asynchronous Code

However, when we want to test the same code, but it runs on an Asynchronous way:

```swift
center.publisher(for: .someNotification)
    .sink { [weak self] _ in
        guard let self else { return }
        Task {
            // Note: We could have some async code here.
            self.number += 1 // -> This is what we want to test
        }
    }
    .store(in: &subscribers)
```

Then we need to use some custom code to test the asynchronous code:

```swift
func test_viewModel_subscriber() {
    // Given
    XCTAssertEqual(sut.number, 0)
    // When
    postAndProcessNotification(
        .someNotification,
        with: center,
        until: { [weak self] in
            self?.sut.number == 1
        }
    )
    // Then
    XCTAssertEqual(sut.number, 1)
}
```

---

* [Blog Post](https://www.manu.show/2023-09-18-notification-center-testing/)