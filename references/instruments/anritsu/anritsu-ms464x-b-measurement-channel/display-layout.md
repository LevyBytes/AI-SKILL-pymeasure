# pymeasure.instruments.anritsu.anritsuMS464xB.MeasurementChannel.display_layout

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *display_layout*: Any*

Set the trace display arrangement for the indicated channel using Row-by-Column format.

Accepted values are: R1C1, R1C2, R2C1, R1C3, R3C1, R2C2C1. Additional accepted values are R2C1C2, C2R2R1, C2R1R2, R1C4, R4C1, R2C2. The remaining accepted values are R2C3, R3C2, R2C4, R4C2, R3C3, R5C2, R2C5, R4C3, R3C4, R4C4. The number after R gives the row count, and the number after C gives the column count; for example, R2C2 creates a 2-by-2 layout. Options containing two C's or two R's create asymmetric layouts; for example, R2C1C2 creates 1 trace on the top row and two traces side-by-side on the bottom row.
