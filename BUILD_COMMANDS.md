# Build Commands for Trave-Social

## Development Build (with EAS)

### Build Dev Client (Internal Distribution)
```bash
eas build --platform android --profile dev
```

### Build Preview (for testing features)
```bash
eas build --platform android --profile preview
```

### Build Production (Release to Play Store)
```bash
eas build --platform android --profile production
```

## Local Android Builds (Gradle)

### Dev Debug Build (APK)
```bash
./gradlew app:assembleDevDebug
# Output: android/app/build/outputs/apk/dev/debug/app-dev-debug.apk
```

### Dev Release Build (APK - Signed)
```bash
./gradlew app:assembleDevRelease
# Output: android/app/build/outputs/apk/dev/release/app-dev-release.apk
```

### Production Debug Build (APK)
```bash
./gradlew app:assembleProdDebug
# Output: android/app/build/outputs/apk/prod/debug/app-prod-debug.apk
```

### Production Release Build (APK - Signed)
```bash
./gradlew app:assembleProdRelease
# Output: android/app/build/outputs/apk/prod/release/app-prod-release.apk
```

### Production Release Bundle (for Play Store)
```bash
./gradlew app:bundleProdRelease
# Output: android/app/build/outputs/bundle/prodRelease/app-prod-release.aab
```

## Build Differences

### Dev Flavor (`com.tauhee56.travesocial.dev`)
- Package name: `com.tauhee56.travesocial.dev`
- App name: "Trave-Social DEV"
- Auth redirect scheme: `trave-social.dev`
- API URL: `https://dev-backend.onrender.com/api`
- Can coexist with production app on same device
- For internal testing and development

### Production Flavor (`com.tauhee56.travesocial`)
- Package name: `com.tauhee56.travesocial`
- App name: "Trave-Social"
- Auth redirect scheme: `trave-social`
- API URL: `https://trave-social-backend.onrender.com/api`
- Release to Play Store

## EAS Build Profiles

### development
- Internal distribution
- Development client enabled
- APK format
- Uses gradleCommand: `:app:assembleDebug`

### dev
- Internal distribution
- Development client enabled
- APK format
- Uses gradleCommand: `:app:assembleDevDebug`
- Package: `com.tauhee56.travesocial.dev`
- Environment: development
- Custom backend URL

### preview
- Internal distribution
- For testing before production
- APK format

### production
- Play Store distribution
- Release build (AAB format)
- Auto-increment version

## Installing Apps on Device

### Install APK
```bash
adb install android/app/build/outputs/apk/dev/debug/app-dev-debug.apk
```

## Tips

- Dev and production builds can run simultaneously on the same device (different package names)
- Always use dev build for development/testing
- Production build should only be used for Play Store releases
- Check `google-services.json` is in project root before building
