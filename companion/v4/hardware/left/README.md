# Companion v3 — Left Hinge Board

KiCad project `pcbvr_left`. Board outline **58.64 × 12.9 mm**, 30 components
(the larger of the two boards — it carries the battery, `BT1`).

| Directory | Contents |
|---|---|
| `kicad/` | `pcbvr_left.kicad_pro`, `.kicad_sch`, `.kicad_pcb`, library tables |
| `fabrication/gerbers-2026-06-01/` | Gerber + drill export, 1 Jun 2026 |
| `fabrication/gerbers-2026-06-01.zip` | The same export, zipped — the package sent to the fab |
| `fabrication/gerbers-2026-06-04/` | A later gerber + drill export, 4 Jun 2026 |
| `fabrication/position/` | `CPL_V4_LEFT.csv`, `pcbvr_left-top.csv`, `pcbvr_left-bottom.pos` |
| `bom/` | `BOM_V4_LEFT_pcbway.csv` (PCBWay format), `pcbvr_left.csv` (KiCad export) |
| `exports/` | `schematic.pdf` |

Symbols and footprints are in [`../shared/symbols/`](../shared/symbols/),
shared with the right board.

## Two gerber exports — pick deliberately

Both sets are this board, exported three days apart and differing in copper
and drill count (52 holes on 1 Jun, 56 on 4 Jun). Neither is marked as the one
that was manufactured, so **do not assume the newer one is correct**. The
zipped 1 Jun package is the likelier candidate for what went to the fab, since
zipping is the last step before upload.

The 4 Jun set arrived in the repository filed under the right board — see
[`../right/README.md`](../right/README.md). It is this board's, not the right
board's.

The current `kicad/` sources have moved on from both exports (backups run to
10 Jun), so re-export before any new fab run rather than reusing either.

## Note on naming

The BOM and position files say `V4` while the board is v3. They came from the
original `pcbv3/` upload that way and were left as-is so they still match the
files sent to the fab. Confirm which revision they describe before reusing.
