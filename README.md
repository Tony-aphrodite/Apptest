# TLBDMManager (Apptest)

A fresh React Native 0.82 project for Android and iOS, created with `@react-native-community/cli` and written in TypeScript. It is the untouched starter app: `App.tsx` renders React Native's built-in welcome screen (`NewAppScreen`). It is meant as a clean base for building and testing a mobile app.

![React Native](https://img.shields.io/badge/React_Native-0.82.1-61DAFB?logo=react&logoColor=black)
![React](https://img.shields.io/badge/React-19.1.1-61DAFB?logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-5.8-3178C6?logo=typescript&logoColor=white)
![Node](https://img.shields.io/badge/Node-%3E%3D20-339933?logo=nodedotjs&logoColor=white)

## Features

- **One TypeScript codebase for Android and iOS**: app name `TLBDMManager`, registered in `index.js`.
- **Safe-area handling**: the app is wrapped in `SafeAreaProvider`, and the insets are passed to the screen through `react-native-safe-area-context`.
- **Light and dark mode**: the status bar style follows the system color scheme (`useColorScheme`).
- **New Architecture enabled**: Fabric/TurboModules (`newArchEnabled=true`) with the Hermes JS engine (`hermesEnabled=true`).
- **Ready-made tooling**: ESLint (`@react-native/eslint-config`), Prettier, and Jest with a render smoke test in `__tests__/App.test.tsx`.

## Tech stack

| Area | Version / setting |
| --- | --- |
| Framework | React Native 0.82.1, React 19.1.1 |
| Language | TypeScript 5.8 (`@react-native/typescript-config`) |
| Bundler | Metro (`@react-native/metro-config`) |
| Android | Kotlin, Gradle 9.0.0 wrapper, minSdk 24, compile/target SDK 36, package `com.tlbdmmanager` |
| iOS | Swift `AppDelegate`, CocoaPods, deployment target iOS 15.1 |
| Testing | Jest 29 with the `react-native` preset, `react-test-renderer` |

## Getting started

### Prerequisites

- Node.js 20 or newer (set in `engines` in `package.json`)
- Follow React Native's [Set Up Your Environment](https://reactnative.dev/docs/set-up-your-environment) guide:
  - Android: Android Studio, the Android SDK and a JDK
  - iOS (macOS only): Xcode, Ruby 2.6.10 or newer, and Bundler for CocoaPods

### Install

```sh
npm install

# iOS only: install CocoaPods with Bundler, then the native pods
bundle install
cd ios && bundle exec pod install && cd ..
```

### Run

```sh
npm start          # start the Metro dev server
npm run android    # build and launch on an Android emulator or device
npm run ios        # build and launch on the iOS Simulator
```

Keep Metro running in its own terminal while you use the `android` / `ios` commands. You can also open `android/` in Android Studio or `ios/TLBDMManager.xcworkspace` in Xcode, after `pod install` has run.

### Quality checks

```sh
npm run lint       # ESLint
npm test           # Jest
```

## Project structure

```
.
├── App.tsx              Root component (safe area + welcome screen)
├── index.js             Registers the app with AppRegistry
├── app.json             App name / display name
├── __tests__/           Jest render test
├── android/             Native Android project (Kotlin, Gradle)
│   └── app/src/main/java/com/tlbdmmanager/   MainActivity, MainApplication
├── ios/                 Native iOS project (Swift, CocoaPods)
│   └── TLBDMManager/    AppDelegate, Info.plist, LaunchScreen
├── metro.config.js, babel.config.js, jest.config.js, tsconfig.json
└── Gemfile              CocoaPods / Ruby gem versions for iOS
```

## Notes

- The Android release build is still signed with the template's debug keystore (`android/app/debug.keystore`). Create your own upload key before publishing to Google Play.
- The iOS bundle identifier still uses the template default (`org.reactjs.native.example.*`). Change it before shipping.
