# TODOs

## When do we use them?
`TODO`s should be used sparingly, but are acceptable in the following conditions:
* To ensure that pull requests are kept small, if there are gaps left in functionality, or stubbed implementations for future pull requests, a `TODO` comment can be used.
* When a task you’re working on is depended on by another task, it might make sense to leave empty implementations with a `TODO` within "hooks" (e.g. button action methods or closures) that will use the functionality introduced in the dependent task.

### Key Considerations
* `TODO`s must always be accompanied by a link to the task description that will replace the `TODO` with intended functionality.
* Do not use `FIXME` or other specifiers for unfinished work. Sticking with one makes it easier to search for known unfinished work, and makes the decision of which to use easier.
* `TODO`s should be specified on single-line and double-slash comments only.

### Example
```swift
@objc private func editButtonTapped(_ sender: UIButton) {
    // TODO: Add proper documentation in the contributing guidelines: [TICKET-URL]
}
```

## Future-Improvement comments
When you find something that could be improved but it's working correctly, add a `// Future-Improvement:` comment.

Future-Improvement comments might or might not be accompanied by a Linear ticket.

### Example:
```swift
// Future-Improvement: Convert sync method to async/await and add unit tests.
```