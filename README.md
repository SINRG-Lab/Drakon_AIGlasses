# Drakon AI Glasses

Hardware, firmware, and 3D models for the Drakon AI smart glasses.

This repository is the single home for everything physical and embedded: board
designs, embedded firmware, and printable frame parts. Application code,
measurement studies, and companion apps live in other repositories.

## Editions

The glasses come in two open-source editions that share a frame and audio
pipeline but differ in how they reach the network.

| Edition | Directory | Connectivity | Status |
|---|---|---|---|
| Companion | [`companion/`](companion/) | Wi-Fi / BLE, relayed via a paired device | v3 fabricated, v4 in design |
| Standalone | [`standalone/`](standalone/) | On-board cellular | v1 in design |

## Versions

Each edition is numbered independently — `companion/v3` and `standalone/v1` are
unrelated designs. Numbering continues each edition's own history, so the
companion boards start at v3 to match the `pcbv3` the team already builds.

| Version | Status |
|---|---|
| [`companion/v3`](companion/v3/) | **Current** — left and right boards fabricated |
| [`companion/v4`](companion/v4/) | Next — in design, empty |
| [`standalone/v1`](standalone/v1/) | First board — in design, empty |

A new version directory is created when the PCB changes in a way that breaks
compatibility with existing firmware or frame parts. Small fixes land in the
existing version. See [`docs/versioning.md`](docs/versioning.md).

## Layout

Every build is **two PCBs**, one per temple, so `hardware/` splits left/right.

```
<edition>/<version>/
├── firmware/            Embedded source for that board version
│   ├── src/  include/  lib/
├── hardware/
│   ├── left/            Left temple board
│   │   ├── kicad/       The KiCad project — .kicad_pro, .kicad_sch, .kicad_pcb
│   │   ├── fabrication/ gerbers/ and position/ files as sent to the fab
│   │   ├── bom/         Bills of materials
│   │   └── exports/     Schematic PDFs, STEP models, renders
│   ├── right/           Right temple board — same layout
│   └── shared/          Symbols, footprints and datasheets used by both
└── 3d-models/
    ├── cad/             Editable CAD source (STEP, SLDPRT, F3D)
    ├── exports/         Print-ready meshes (STL, 3MF)
    └── renders/         Images for docs and papers

common/                  Shared across editions and versions
├── firmware/  hardware/  3d-models/  scripts/

docs/
├── specs/  assembly/  bring-up/  versioning.md
```

## Conventions

- **Keep each KiCad project in one directory.** `.kicad_pro`, `.kicad_sch` and
  `.kicad_pcb` must sit together under `kicad/` or the project will not open.
- **Put a file under `common/` only once a second edition or version actually
  uses it.** Premature sharing is harder to undo than duplication.
- **Commit CAD source alongside exports.** An STL with no editable source is a
  dead end.
- **Commit fabrication outputs even though they are generated.** They are the
  exact files sent to the fab; regenerating from a newer KiCad will not
  reproduce what was actually built.
- **Never commit secrets.** Firmware credentials belong in an ignored
  `config.h` beside a committed `config.h.template`.
- **Do not commit KiCad backups, `fp-info-cache`, or `.kicad_prl`.** They are
  local caches and editor state; `.gitignore` covers them.

## Git LFS

CAD, mesh, fabrication and datasheet binaries are tracked with
[Git LFS](https://git-lfs.com) — see [`.gitattributes`](.gitattributes). Run
this once per clone, before adding any such files:

```
git lfs install
```

Note that binaries committed before LFS was configured remain ordinary blobs in
history. Converting them requires `git lfs migrate`, which rewrites history and
needs a force-push — coordinate with the team before doing it.
