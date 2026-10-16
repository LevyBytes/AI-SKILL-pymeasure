# Version 0.14.0 (2024-05-22) — Instruments mechanics

- A SCPI base class, `SCPIMixin`, was added to replace `includeSCPI=True` (@BenediktBurger, #905, #1007, #1019, #1047).

- SCPI instruments now include the `next_error` property (@BenediktBurger, #1024).

- `wait_for` now defaults to `query_delay=None` (@BenediktBurger, #1077).

- The default empty dictionary used by `expected_protocol` was fixed (@BenediktBurger, #1087).

- Automatic importing of every instrument from `pymeasure/instruments/__init__.py`` was removed (@mcdo0486, #919).

- `find_serial_port` was added to locate a serial port from USB information (@BenediktBurger, #982).
