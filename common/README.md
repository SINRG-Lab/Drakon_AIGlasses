# Common

Assets shared across more than one edition or revision.

- [`firmware/`](firmware/) — libraries used by more than one build
- [`hardware/`](hardware/) — KiCad symbols, footprints, and shared datasheets
- [`3d-models/`](3d-models/) — parts common to every build, e.g. the charging cradle
- [`scripts/`](scripts/) — flashing, export, and build helpers

Move something here only once a second edition or revision actually uses it.
Code that lives in `common/` is code that cannot be changed for one board
without checking every other board, so the bar for adding to it is a real
second consumer — not an anticipated one.
