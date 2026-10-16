# pymeasure.instruments.kepco.KepcoBOP3612.operating_mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *operating_mode*: Any*

Set or query the BOP operating mode.

For commands, send the string VOLT or CURR. Queries return 0 or 1, corresponding respectively to VOLT or CURR; the driver maps that value back to the matching string.
