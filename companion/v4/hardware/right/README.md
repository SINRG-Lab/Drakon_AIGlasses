# Companion v3 — Right Hinge Board

KiCad project `pcb_right`. Board outline **40.0 × 20.2 mm**, 16 components —
a smaller board than the left, with no battery.

| Directory | Contents |
|---|---|
| `kicad/` | `pcb_right.kicad_pro`, `.kicad_sch`, `.kicad_pcb`, library tables |
| `fabrication/position/` | `CPL_V4_RIGHT.csv`, `pcb_right-top.CSV` |
| `bom/` | `BOM_V4_RIGHT.csv`, `pcb_right.csv` |
| `exports/` | `pcb_right.step` |

Symbols and footprints are in [`../shared/symbols/`](../shared/symbols/),
shared with the left board.

## ⚠ No gerbers exist for this board

The original upload had a folder called `pcbv3_right_frabrication_files`, but
its `gerber/` subfolder did **not** contain this board. Those files were a
second export of the *left* board, and have been moved to
[`../left/fabrication/gerbers-2026-06-04/`](../left/fabrication/gerbers-2026-06-04/).

Three independent checks agree:

| Check | Left board | Right board | The misfiled gerbers |
|---|---|---|---|
| Edge cuts outline | 58.64 × 12.9 mm | 40.0 × 20.2 mm | 58.64 × 12.9 mm |
| Drill-pattern match | — | 2.1% | 70.8% to the left board |
| `%TF.ProjectId` | `pcbvr_left` | — | `pcbvr_left` |

**Anyone who sent that folder to a fab would have received a second left
board.** Export gerbers from `kicad/pcb_right.kicad_pcb` before ordering.

The BOM and position files in this directory *are* genuinely this board — their
designators (`C1`–`C4`, `FB1`, `FB2`, `J1`, `J2`, `R1`–`R3`, `SW1`, `U1`, `U2`)
all fall within its 16 components and include none of the left board's
battery, diodes or extra passives. Only the gerbers were misfiled.
