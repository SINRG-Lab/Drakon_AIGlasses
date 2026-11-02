# iOSGlasses companion app

SwiftUI iPhone app for the [XIAO ESP32-S3 Sense firmware](../firmware/S3_App_V2/).
Includes BLE voice/control, optional Wi-Fi photo transfer, a gallery, and a
Live Activity widget. Requires iOS 17 or later; use Xcode with Swift 6 support.

## Xcode setup

1. Open `companion/ios/iOSGlasses.xcodeproj` from the repository root.
2. Allow Swift Package Manager to resolve the committed `Package.resolved`
   dependencies, including `supabase-swift`.
3. Select the `iOSGlasses` scheme. For a physical iPhone, select your signing
   team for the app, widget and tests, and adjust bundle identifiers if needed.
4. Build and run. Allow Bluetooth and local-network access when requested.

The imported signing team is the upstream development setting. Simulator builds
can disable signing without changing the project:

```sh
xcodebuild -project companion/ios/iOSGlasses.xcodeproj -scheme iOSGlasses \
  -destination 'generic/platform=iOS Simulator' \
  -derivedDataPath /tmp/drakon-ios-build CODE_SIGNING_ALLOWED=NO build
```

Run the existing voice-session tests on an installed simulator (replace the
destination with a device listed by `xcrun simctl list devices available`):

```sh
xcodebuild -project companion/ios/iOSGlasses.xcodeproj -scheme iOSGlasses \
  -destination 'platform=iOS Simulator,name=iPhone 17 Pro,OS=26.5' \
  -derivedDataPath /tmp/drakon-ios-build CODE_SIGNING_ALLOWED=NO test
```

## Backend

`iOSGlasses/SupabaseRealtimeService.swift` retains the upstream Supabase project
URL and public publishable key. Voice sessions require that project's anonymous
authentication and `realtime-session` Edge Function, which returns short-lived
Realtime credentials. The backend is maintained separately and is not included
here. For another deployment, change those public client settings and deploy a
compatible backend. Permanent API keys and service-role secrets belong on the
backend, never in the app.

## Connect to the glasses

1. Flash and power the XIAO with the matching wiring and firmware.
2. Use the app's glasses scan/connect controls to connect to `AIGlasses-ESP32S3`.
3. Use the physical button for voice questions and photo gestures described in
   the [firmware README](../firmware/S3_App_V2/README.md#gestures).
4. BLE alone supports voice and photos. For optional bulk photo transfer, enable
   Wi-Fi in the app and manually join the glasses hotspot using its displayed
   SSID/password, then return to the app. Keep phone internet access available
   for voice sessions.

The simulator checks app compilation and voice-session policies. Bluetooth,
hotspot switching, cloud sessions, microphone, camera and speaker behavior need
physical-device verification.

Source commit and import details are recorded in the
[companion README](../README.md#source).
