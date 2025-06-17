# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an iOS application called "Arrgh" built with SwiftUI and SwiftData. It's a cross-platform app supporting iOS, iPadOS, macOS, and visionOS.

## Build Commands

```bash
# Build for iOS Simulator
xcodebuild -project Arrgh/Arrgh.xcodeproj -scheme Arrgh -destination 'platform=iOS Simulator,name=iPhone 15'

# Run unit and UI tests
xcodebuild test -project Arrgh/Arrgh.xcodeproj -scheme Arrgh -destination 'platform=iOS Simulator,name=iPhone 15'

# Build for specific platforms
xcodebuild -project Arrgh/Arrgh.xcodeproj -scheme Arrgh -destination 'platform=macOS'
xcodebuild -project Arrgh/Arrgh.xcodeproj -scheme Arrgh -destination 'platform=visionOS Simulator,name=Apple Vision Pro'

# Clean build
xcodebuild clean -project Arrgh/Arrgh.xcodeproj -scheme Arrgh

# Build for release
xcodebuild -project Arrgh/Arrgh.xcodeproj -scheme Arrgh -configuration Release archive
```

## Architecture

The app follows SwiftUI's declarative architecture pattern:

1. **Entry Point**: `Arrgh/Arrgh/ArrghApp.swift` - The `@main` struct that configures the app's scenes and SwiftData ModelContainer
2. **Main View**: `Arrgh/Arrgh/ContentView.swift` - Uses NavigationSplitView with platform-specific adaptations
3. **Data Model**: `Arrgh/Arrgh/Item.swift` - SwiftData model using `@Model` macro for persistence
4. **Testing**: 
   - Unit tests use the new Swift Testing framework with `@Test` attributes
   - UI tests use XCTest framework

## Key Technical Details

- **Bundle ID**: `com.paulbonneville.Arrgh`
- **Minimum Deployment Targets**: iOS 26.0, macOS 15.5, visionOS 26.0
- **Swift Version**: 5.0
- **Data Persistence**: SwiftData with automatic ModelContainer setup
- **Background Capabilities**: Remote notifications enabled in entitlements

## Development Notes

- The project uses cutting-edge Apple frameworks (SwiftData, Swift Testing) that require Xcode 26.0 Beta
- No external dependencies or package managers are used
- Platform-specific code uses `#if os()` compiler directives
- The app includes both unit tests (Swift Testing) and UI tests (XCTest)