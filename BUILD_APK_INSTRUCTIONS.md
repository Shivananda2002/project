# Building APK Instructions

This guide will help you build an APK file from your React app using Capacitor.

## Prerequisites

1. **Install Android Studio**: Download and install Android Studio from [developer.android.com](https://developer.android.com/studio)
2. **Install Java JDK 17**: Make sure you have Java JDK 17 installed
3. **Set up Android SDK**: Through Android Studio, install Android SDK (API level 34)
4. **Set Environment Variables**:
   ```bash
   export ANDROID_HOME=$HOME/Android/Sdk
   export PATH=$PATH:$ANDROID_HOME/emulator
   export PATH=$PATH:$ANDROID_HOME/platform-tools
   export PATH=$PATH:$ANDROID_HOME/cmdline-tools/latest/bin
   export JAVA_HOME=/path/to/your/java17
   ```

## Build Steps

### 1. Initialize Capacitor Android Platform
```bash
npm run android:init
```

### 2. Build and Sync
```bash
npm run android:build
```

### 3. Open in Android Studio
```bash
npm run android:open
```

### 4. Build APK in Android Studio
1. In Android Studio, go to **Build** → **Build Bundle(s) / APK(s)** → **Build APK(s)**
2. Wait for the build to complete
3. Click "locate" to find your APK file

### 5. Alternative: Build APK via Command Line
```bash
npm run android:release
```

The APK will be generated at: `android/app/build/outputs/apk/release/app-release.apk`

## Testing

### Run on Emulator
```bash
npm run android:run
```

### Install APK on Device
```bash
adb install android/app/build/outputs/apk/release/app-release.apk
```

## App Configuration

- **App ID**: `com.imirror.app`
- **App Name**: `I Mirror`
- **Version**: `1.0.0`
- **Min SDK**: 22 (Android 5.1)
- **Target SDK**: 34 (Android 14)

## Features Included

- ✅ Splash Screen with app branding
- ✅ Status Bar styling
- ✅ Keyboard handling
- ✅ Haptic feedback support
- ✅ Back button handling
- ✅ App state management
- ✅ File provider for camera/storage access
- ✅ Network permissions for API calls

## Troubleshooting

### Common Issues:

1. **Gradle Build Failed**: Make sure you have the correct Java version (17)
2. **SDK Not Found**: Verify ANDROID_HOME is set correctly
3. **Permission Denied**: Run `chmod +x android/gradlew`
4. **Build Tools Missing**: Install build-tools via Android Studio SDK Manager

### Clean Build:
```bash
cd android
./gradlew clean
cd ..
npm run android:build
```

## Signing for Release

For production release, you'll need to sign your APK:

1. Generate a keystore:
```bash
keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
```

2. Add signing config to `android/app/build.gradle`
3. Build signed APK

## App Store Deployment

1. Create a Google Play Console account
2. Upload your signed APK/AAB
3. Fill in app details and screenshots
4. Submit for review

Your app is now ready to be built as an APK! 🚀