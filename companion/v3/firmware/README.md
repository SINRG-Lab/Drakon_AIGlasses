# Firmware — companion/v3

This directory is a placeholder for embedded source targeting the ESP32-C6 v3
boards. The imported XIAO ESP32-S3 Sense development sketch lives at
[`../../firmware/S3_App_V2/`](../../firmware/S3_App_V2/); it uses a different
pin map and does not target these boards.

- `src/` — application and driver sources
- `include/` — public headers
- `lib/` — vendored or project-local libraries

Credentials go in `src/config.h`, which is gitignored. Commit a
`src/config.h.template` with the values blanked so others know what to fill in.

Firmware releases are tagged `companion/v3/vX.Y.Z` rather than kept in separate
directories — the directory says which board, the tag says which build.
