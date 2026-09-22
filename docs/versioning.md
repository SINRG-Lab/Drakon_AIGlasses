# Versioning

## Editions

An **edition** is a product line with its own board family. Editions live at the
top level: `companion/` and `standalone/`. A new edition is added only for a
fundamentally different product, not for a component swap.

## Versions

A **version** is a board version within an edition: `v1`, `v2`, `v3`, and so on.
Each version directory holds the firmware, hardware design, and frame parts that
belong together as one buildable unit.

Editions are numbered independently, each continuing its own history:

- `companion/` starts at **v3**, matching the `pcbv3` the team already builds.
  v1 and v2 predate this repository.
- `standalone/` starts at **v1** — no board has been fabricated yet.

`companion/v3` and `standalone/v1` are unrelated designs, and a shared number
between editions would mean nothing.

Each version is two PCBs, one per temple, under `hardware/left/` and
`hardware/right/`.

### When to create a new version

Create one when the board changes in a way that breaks compatibility with
existing firmware or frame parts:

- Pin assignments change, or a peripheral is added or removed
- The board outline changes enough that the frame no longer fits
- A component swap requires a different driver

### When not to

Fix it in place, in the existing version directory:

- Silkscreen, labelling, or documentation corrections
- Component substitutions that are drop-in compatible
- Firmware bug fixes and features on unchanged hardware

### Lifecycle

| Stage | Meaning |
|---|---|
| In design | Schematic and layout in progress; nothing fabricated |
| Prototype | Boards fabricated and in bring-up |
| Current | Validated; the version to build against |
| Superseded | A later version has taken over; kept for reference |

Record the current stage in each version's `README.md`. Version directories are
never deleted — a superseded version stays as the reference for hardware already
in the field.

Create the next version's directory when design work on it actually starts, not
in advance.

## Firmware versions

Firmware is tagged, not directory-versioned. Use
`<edition>/<version>/vX.Y.Z` — for example `companion/v3/v1.2.0`. The version
directory says which board the firmware targets; the tag says which build of
that firmware it is.
