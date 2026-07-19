---
name: feature-or-refactor-menu-bar-tabs
description: Workflow command scaffold for feature-or-refactor-menu-bar-tabs in ClashBar.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /feature-or-refactor-menu-bar-tabs

Use this workflow when working on **feature-or-refactor-menu-bar-tabs** in `ClashBar`.

## Goal

Implements or refactors features in the menu bar tabs, including UI/UX improvements, new actions, layout changes, or proxy-related enhancements.

## Common Files

- `Sources/ClashBar/Features/MenuBar/Tabs/*.swift`
- `Sources/ClashBar/Features/MenuBar/Components/*.swift`
- `Sources/ClashBar/Features/MenuBar/Layout/*.swift`
- `Sources/ClashBar/App/State/AppState+*.swift`
- `Sources/ClashBar/Resources/Localization/*.lproj/Localizable.strings`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or add files in Sources/ClashBar/Features/MenuBar/Tabs/* (such as ActivityTabView.swift, ProxyProvidersAndGroupsView.swift, SystemTabView.swift, etc.)
- Update shared menu bar components in Sources/ClashBar/Features/MenuBar/Components/* or layout helpers in Sources/ClashBar/Features/MenuBar/Layout/*
- Optionally update related state in Sources/ClashBar/App/State/AppState+*.swift
- Optionally update localization files if UI text is changed

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.