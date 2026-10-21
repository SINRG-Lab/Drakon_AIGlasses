# Drakon — Companion Edition

The companion-linked build. The glasses handle capture, audio I/O and local
processing; network access is relayed through a paired phone or host over
Wi-Fi/BLE.

The v3 boards use a Seeed XIAO **ESP32-C6** with a MAX98357A I2S amplifier and a CUI
CMS-15116-SP speaker. Compared to the [Standalone Edition](../standalone/),
this build trades untethered operation for lower cost, lower power and a
smaller board.

| Version | Status | Notes |
|---|---|---|
| [`v3`](v3/) | **Current** | Left and right boards fabricated; KiCad sources and fab outputs in repo |
| [`v4`](v4/) | In design | Empty — scaffold only |

Numbering starts at v3 because v1 and v2 predate this repository.

## Software

The XIAO development software used alongside the MK3.5 work is included here:

| Directory | Contents | Target |
|---|---|---|
| [`firmware/S3_App_V2/`](firmware/S3_App_V2/) | Arduino sketch, drivers, BLE/Wi-Fi protocol and wiring docs | Seeed XIAO ESP32-S3 Sense |
| [`ios/`](ios/) | iOSGlasses Xcode project, Live Activity widget and voice-session tests | iPhone, iOS 17+ |

The XIAO sketch uses the Sense camera and PDM microphone, external MAX98357A
amplifiers, and a push-to-talk button. BLE carries control and voice; optional
Wi-Fi carries photos. Read the [wiring map](firmware/S3_App_V2/docs/HARDWARE.md)
before flashing. The ESP32-C6 v3 boards above and the custom ESP32-S3-PICO MK3.5
PCB use different hardware; this sketch does not target either board. Software
stays at edition level so it is not mistaken for board-qualified v3 firmware.

### Build the XIAO firmware

Install Arduino CLI, the Espressif board package, and NimBLE-Arduino. The import
is checked with ESP32 Arduino core **3.3.11** and NimBLE-Arduino **2.5.1**:

```sh
arduino-cli core install esp32:esp32@3.3.11 --additional-urls https://espressif.github.io/arduino-esp32/package_esp32_index.json
arduino-cli lib install 'NimBLE-Arduino@2.5.1'
arduino-cli compile --fqbn 'esp32:esp32:XIAO_ESP32S3:PSRAM=opi' companion/firmware/S3_App_V2
```

Run from the repository root. For Arduino IDE setup, upload instructions, gestures
and tuning, see the [firmware README](firmware/S3_App_V2/README.md). Its `config.h`
contains board and protocol defaults, including a shared development AP password;
it contains no personal Wi-Fi or cloud credentials. Keep private credentials out
of committed files.

### Build and connect the iOS app

See [`ios/README.md`](ios/README.md) for Xcode setup, simulator checks, backend
requirements, and pairing. Real BLE, camera and audio operation requires an
iPhone and the wired XIAO hardware; simulator tests do not verify those paths.

### Source

Imported from [`SINRG-Lab/AIGlasses`, branch `camilo`, commit
`9ef7c6d4e3d632fdd713f9a4234eaaefe206baa5`](https://github.com/SINRG-Lab/AIGlasses/tree/9ef7c6d4e3d632fdd713f9a4234eaaefe206baa5):
`S3_App_V2/` → `companion/firmware/S3_App_V2/`, and `iOSGlasses/` → `companion/ios/`.
Only committed source was imported; local MK3.5 PCB changes, Xcode user state,
and build outputs were excluded. The iOS Foundation framework reference was made
relative to the selected SDK so it does not require the original iOS 18 SDK path.
