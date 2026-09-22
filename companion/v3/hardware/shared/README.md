# Companion v3 — Shared Hardware Libraries

Symbols, footprints and 3D part models used by both temple boards.

- `symbols/` — KiCad symbol libraries and `.pretty` footprint directories
- `footprints/` — standalone footprints not part of a symbol library
- `datasheets/` — datasheets for parts on these boards

The original upload carried a separate copy of these libraries under each
board. The two copies were byte-identical apart from two footprints
(`c6.pretty/AK1.kicad_mod` and `c6.pretty/LOGO_MAIN_1.kicad_mod`) present only
in the left one, so they were merged into this single superset.

Board projects reference these through their `fp-lib-table` and `sym-lib-table`.
If a project fails to resolve a symbol after the move, fix the path there.

## Key parts

| Library | Part |
|---|---|
| `c6.pretty` | Seeed XIAO ESP32-C6 module, plus SINRG/NEU logo footprints |
| `MAX98357AETE_T` | MAX98357A I2S class-D amplifier |
| `CMS-15116-SP` | CUI CMS-15116-SP speaker |
| `HRS_TF31-6S-0.5SH_800_.pretty` | Hirose TF31 6-pin FPC connector |
