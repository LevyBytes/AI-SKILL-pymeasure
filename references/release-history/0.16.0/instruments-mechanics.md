# Version 0.16.0 (2026-05-20) — Instruments mechanics

- Prologix adapter support now includes `_write_bytes()` and `_read_bytes()` (@dl8dtl, #1259).

- `list_resources()` now handles SerialException (@hvegh, #1287).

- `get_process_list` was added and made dynamic (@BenediktBurger, @Falk3579, #1291, #1313, #1315).

- Typing was added to `expected_protocol`, adapters, and `Instrument` (@BenediktBurger, #1084, #1331).

- Property creator docstring lists now include a concrete hint (@BenediktBurger, #1281).

- A SCPI mixin test was added for devices (@fg-lumentum, #1391).

- Update Prologix documentation (@dl8dtl, #1272)
