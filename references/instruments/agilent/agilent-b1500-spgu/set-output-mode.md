# pymeasure.instruments.agilent.agilentB1500.SPGU.set_output_mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_output_mode(*mode*, *condition=None*)

Configure operating mode for SPGU channel outputs. (`SPRM`)

The setting affects every SPGU module installed in the B1500.

Parameters:

- **mode** (*SPGUOperationMode*) – SPGU operation mode

- **condition** (*int** or **float** or **None*) – Pulse count for `SPGUOutputMode.COUNT` or output duration for `SPGUOutputMode.DURATION`; ignored for `SPGUOutputMode.FREE_RUN`
