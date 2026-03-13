# ClashBar Development Patterns

> Auto-generated skill from repository analysis

## Overview

ClashBar is a Swift-based macOS menu bar application that provides system-level controls and monitoring. The codebase follows a modular architecture with state management, localization support, and a SwiftUI-based interface. The project emphasizes clean separation between UI components, application state, and system integration.

## Coding Conventions

### File Naming
- Use PascalCase for all Swift files: `StatusItemController.swift`, `MenuBarCommonViews.swift`
- Extensions follow the pattern: `AppState+FeatureName.swift`
- Tab-specific views: `SystemTabView.swift`, `SystemTabView+Rows.swift`

### Code Structure
```swift
// File organization follows feature-based structure
Sources/ClashBar/
├── App/State/           # Application state management
├── Features/MenuBar/    # Menu bar UI components
├── UI/Shared/          # Reusable UI components
└── Resources/          # Assets and localization
```

### Commit Style
- Use conventional commits with prefixes: `feat:`, `fix:`, `refactor:`, `docs:`, `perf:`, `chore:`
- Keep commit messages concise (~49 characters average)
- Example: `feat: add network monitoring to status item`

## Workflows

### Documentation Update
**Trigger:** When updating project documentation, README, or visual assets
**Command:** `/update-docs`

1. Update `README.md` with new features or instructions
2. Refresh screenshots in `imgs/` directory (PNG/SVG format)
3. Update `CHANGELOG.md` with version information and changes
4. Ensure all asset references are working correctly

```markdown
## Example README structure
# ClashBar
[Description]
## Features
- Feature list with screenshots from imgs/
```

### Localization Update
**Trigger:** When adding new UI text or updating translations
**Command:** `/add-localization`

1. Add new strings to `en.lproj/Localizable.strings`:
```swift
"new_feature_title" = "New Feature";
"new_feature_description" = "Description of the new feature";
```

2. Add corresponding Chinese translations to `zh-Hans.lproj/Localizable.strings`:
```swift
"new_feature_title" = "新功能";
"new_feature_description" = "新功能的描述";
```

3. Update UI components to use localized strings:
```swift
Text("new_feature_title".localized)
```

### App State Feature Extension
**Trigger:** When adding new app-level functionality or state management
**Command:** `/extend-app-state`

1. Create or update feature-specific extension: `AppState+NewFeature.swift`
```swift
extension AppState {
    func updateNewFeature(_ value: NewFeatureType) {
        // Implementation
    }
}
```

2. Update main `AppState.swift` with new properties
3. Add new types to `AppStateTypes.swift` if needed
4. Update related UI components to consume new state

### Menu Bar UI Enhancement
**Trigger:** When improving or adding menu bar interface components
**Command:** `/enhance-menu-bar`

1. Update shared components in `MenuBarCommonViews.swift`:
```swift
struct NewMenuBarComponent: View {
    var body: some View {
        // Component implementation
    }
}
```

2. Modify specific tab views in `Tabs/` directory
3. Update `MenuBarRoot.swift` for layout changes
4. Adjust layout tokens and spacing as needed

### Status Item Refinement
**Trigger:** When improving the status bar item appearance or behavior
**Command:** `/refine-status-item`

1. Update `StatusItemContentView.swift` for visual changes:
```swift
var body: some View {
    HStack {
        // Updated status item content
    }
    .background(Color.clear)
}
```

2. Modify `StatusItemController.swift` for behavior changes
3. Test appearance in both light and dark macOS themes
4. Ensure proper scaling for different screen densities

### Brand Asset Update
**Trigger:** When updating app branding, icons, or visual identity
**Command:** `/update-branding`

1. Update icon files in `Resources/Brand/` directory
2. Update `Package.swift` with new asset references
3. Run preprocessing script: `Scripts/preprocess.sh`
4. Update `BrandIcon.swift` component if needed:
```swift
struct BrandIcon: View {
    let size: CGFloat
    
    var body: some View {
        Image("brand_icon")
            .resizable()
            .frame(width: size, height: size)
    }
}
```

5. Refresh README screenshots to reflect new branding

### System Tab Feature Addition
**Trigger:** When adding new system configuration options or controls
**Command:** `/add-system-feature`

1. Update `SystemTabView.swift` with new UI elements
2. Add setting rows to `SystemTabView+Rows.swift`:
```swift
private var newFeatureRow: some View {
    HStack {
        Text("new_feature_title".localized)
        Spacer()
        Toggle("", isOn: $appState.newFeatureEnabled)
    }
}
```

3. Add corresponding AppState extensions for new functionality
4. Update localization strings for new settings

## Testing Patterns

The codebase uses a pattern-based testing approach:
- Test files follow the `*.test.*` naming convention
- Focus on state management and UI component testing
- Test both English and Chinese localizations
- Verify menu bar behavior across different macOS versions

## Commands

| Command | Purpose |
|---------|---------|
| `/update-docs` | Update README, changelog, and project assets |
| `/add-localization` | Add or update English and Chinese translations |
| `/extend-app-state` | Add new app-level functionality and state management |
| `/enhance-menu-bar` | Improve menu bar UI components and layout |
| `/refine-status-item` | Update status bar item appearance and behavior |
| `/update-branding` | Update brand icons and visual assets |
| `/add-system-feature` | Add new system configuration options |