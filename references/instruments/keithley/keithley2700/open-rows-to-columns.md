# pymeasure.instruments.keithley.Keithley2700.open_rows_to_columns

[Owning PyMeasure class, adapter and connection contract](overview.md)

open_rows_to_columns(*rows*, *columns*, *slot=None*)

Open, meaning disconnect, the 7709 connection matrix channels between the chosen column(s) and row(s). Only one of "rows" or "columns" can be "all"

Parameters:

- **rows** – row number, list of numbers, or "all"

- **columns** – column number, list of numbers, or "all"

- **slot** – slot number (1 or 2) for the 7709 card to use. (default: `None`)
