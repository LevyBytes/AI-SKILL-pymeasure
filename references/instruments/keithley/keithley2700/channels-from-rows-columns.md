# pymeasure.instruments.keithley.Keithley2700.channels_from_rows_columns

[Owning PyMeasure class, adapter and connection contract](overview.md)

channels_from_rows_columns(*rows*, *columns*, *slot=None*)

Compute the 7709 connection matrix channel numbers for the supplied column(s) and row(s). Returns a list of channel numbers. Only one of "rows" or "columns" can be "all"

Parameters:

- **rows** – row number, list of numbers, or "all"

- **columns** – column number, list of numbers, or "all"

- **slot** – slot number (1 or 2) for the 7709 card to use. (default: `None`)
