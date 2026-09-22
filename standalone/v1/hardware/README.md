# Hardware — standalone/v1

Two boards, one per temple.

- [`left/`](left/) — left temple board
- [`right/`](right/) — right temple board
- [`shared/`](shared/) — symbols, footprints and datasheets used by both

Each board directory holds:

| Directory | Contents |
|---|---|
| `kicad/` | The KiCad project. `.kicad_pro`, `.kicad_sch` and `.kicad_pcb` must stay together here or the project will not open. |
| `fabrication/` | `gerbers/` and `position/` exactly as sent to the fab |
| `bom/` | Bills of materials |
| `exports/` | Schematic PDFs, STEP models, renders |

Do not commit `*-backups/`, `fp-info-cache` or `*.kicad_prl` — they are local
caches and editor state, and `.gitignore` already covers them.
