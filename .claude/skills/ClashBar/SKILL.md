```markdown
# ClashBar Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you the core development patterns, coding conventions, and collaborative workflows used in the ClashBar Swift codebase. ClashBar is a macOS menu bar application (no external frameworks detected) with a focus on modular features, clean state management, and robust localization. The repository follows conventional commit messages, enforces consistent code style, and uses a set of repeatable workflows for features, localization, CI, and documentation.

## Coding Conventions

**File Naming**

- Use PascalCase for all Swift files.
  - Example: `ActivityTabView.swift`, `AppStateTypes.swift`

**Import Style**

- Use absolute imports.
  - Example:
    ```swift
    import Foundation
    import AppKit
    ```

**Export Style**

- Mixed: Both explicit and implicit exports are used.
  - Example (explicit):
    ```swift
    public struct ProxyProvider { ... }
    ```
  - Example (implicit, via internal):
    ```swift
    struct SystemTabView { ... }
    ```

**Commit Messages**

- Follow [Conventional Commits](https://www.conventionalcommits.org/) with these prefixes:
  - `fix`, `feat`, `refactor`, `docs`, `chore`, `perf`, `style`
- Typical commit message:
  ```
  feat: add latency indicator to proxy tab
  ```

**Localization**

- All user-facing strings are localized.
- Update both `en.lproj` and `zh-Hans.lproj` for new or changed UI text.

**Testing**

- Test files follow the pattern: `*.test.*`
- Testing framework is not explicitly detected; follow the pattern for placement.

## Workflows

### Feature or Refactor Menu Bar Tabs
**Trigger:** When adding, improving, or refactoring menu bar tab features or layout  
**Command:** `/menu-bar-feature`

1. Edit or add files in `Sources/ClashBar/Features/MenuBar/Tabs/*` (e.g., `ActivityTabView.swift`)
2. Update shared components in `Sources/ClashBar/Features/MenuBar/Components/*` or layout helpers in `Sources/ClashBar/Features/MenuBar/Layout/*`
3. Optionally update related state in `Sources/ClashBar/App/State/AppState+*.swift`
4. Update localization files if UI text changes

**Example:**
```swift
// Sources/ClashBar/Features/MenuBar/Tabs/ProxyProvidersAndGroupsView.swift
struct ProxyProvidersAndGroupsView: View {
    var body: some View {
        Text(NSLocalizedString("Proxy Providers", comment: ""))
    }
}
```

### Update Localization
**Trigger:** When adding or changing user-facing UI text  
**Command:** `/update-localization`

1. Edit or add features/components that introduce new UI text
2. Update `Sources/ClashBar/Resources/Localization/en.lproj/Localizable.strings`
3. Update `Sources/ClashBar/Resources/Localization/zh-Hans.lproj/Localizable.strings`

**Example:**
```swift
// In Swift code
Text(NSLocalizedString("Connection Failed", comment: ""))

// In Localizable.strings (English)
"Connection Failed" = "Connection Failed";

// In Localizable.strings (Simplified Chinese)
"Connection Failed" = "连接失败";
```

### Feature or Refactor App State
**Trigger:** When adding or modifying app state management, polling, config, or settings logic  
**Command:** `/app-state-feature`

1. Edit or add files in `Sources/ClashBar/App/State/AppState+*.swift`
2. Optionally update `AppState.swift` and `AppStateTypes.swift`
3. Optionally update related models in `Sources/ClashBar/Domain/Models/*`
4. Optionally update menu bar components if UI is affected

**Example:**
```swift
// Sources/ClashBar/App/State/AppState+Polling.swift
extension AppState {
    func startPolling() {
        // polling logic here
    }
}
```

### CI Workflow Update
**Trigger:** When adding or changing CI/CD checks  
**Command:** `/ci-update`

1. Edit or add `.github/workflows/build.yml` or other workflow files
2. Optionally update related scripts or documentation

**Example:**
```yaml
# .github/workflows/build.yml
name: Build and Test
on: [push, pull_request]
jobs:
  build:
    runs-on: macos-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build
        run: xcodebuild -scheme ClashBar -sdk macosx
```

### Documentation README Update
**Trigger:** When updating project documentation or legal info  
**Command:** `/update-readme`

1. Edit `README.md`
2. Optionally update `LICENSE` if legal info changes

### Merge Dev to Main
**Trigger:** When releasing a batch of features/fixes from dev to main  
**Command:** `/merge-dev`

1. Merge `dev` branch into `main`
2. All files touched in previous feature/fix commits are included

## Testing Patterns

- Test files are named with the pattern `*.test.*`
- Place test files alongside or near the code under test.
- Example:
  ```
  Sources/ClashBar/Features/MenuBar/Tabs/ProxyProvidersAndGroupsView.test.swift
  ```
- Testing framework is not specified; follow Swift testing best practices.

## Commands

| Command            | Purpose                                         |
|--------------------|-------------------------------------------------|
| /menu-bar-feature  | Add or refactor menu bar tab features/layout    |
| /update-localization | Update localized strings for UI changes        |
| /app-state-feature | Add or modify application state logic           |
| /ci-update         | Update CI/CD workflows                          |
| /update-readme     | Update README or license documentation          |
| /merge-dev         | Merge dev branch into main for release          |
```
