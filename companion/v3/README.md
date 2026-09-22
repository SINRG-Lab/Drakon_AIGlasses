# Drakon Companion Edition — v3

**Status:** Current — both boards fabricated.

| | |
|---|---|
| Edition | Companion Edition |
| Version | `v3` |
| Connectivity | Wi-Fi / BLE via a paired device |
| SoC | Seeed XIAO ESP32-C6 |
| Boards | left + right temple |

## Contents

- [`firmware/`](firmware/) — embedded source for this board version
- [`hardware/`](hardware/) — KiCad projects, fabrication outputs, BOMs
- [`3d-models/`](3d-models/) — frame and enclosure CAD plus print exports

## Open items

- **The right hinge board has no gerbers.** What shipped in the original upload
  as the right board's fabrication output was a second export of the left
  board. See [`hardware/right/README.md`](hardware/right/README.md).
- **The left board has two gerber exports** (1 Jun and 4 Jun 2026) and neither
  is marked as manufactured. See [`hardware/left/README.md`](hardware/left/README.md).
- BOM and position files are named `V4` on a v3 board.
