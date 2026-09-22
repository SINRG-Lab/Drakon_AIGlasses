# Firmware — companion/v4

Embedded source targeting this board version.

- `src/` — application and driver sources
- `include/` — public headers
- `lib/` — vendored or project-local libraries

Credentials go in `src/config.h`, which is gitignored. Commit a
`src/config.h.template` with the values blanked so others know what to fill in.

Firmware releases are tagged `companion/v4/vX.Y.Z` rather than kept in separate
directories — the directory says which board, the tag says which build.
