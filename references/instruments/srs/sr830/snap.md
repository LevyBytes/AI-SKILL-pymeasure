# pymeasure.instruments.srs.SR830.snap

[Owning PyMeasure class, adapter and connection contract](overview.md)

snap(*val1='X'*, *val2='Y'*, **vals*)

Record and retrieve 2 to 6 parameters at the same instant. Supported parameters include X, Y, R, and Theta.
Additional supported parameters include Aux In 1, Aux In 2, and Aux In 3.
The list also includes Aux In 4, Frequency, CH1, and CH2.
Defaults are “X” and “Y”.

Parameters:

- **val1** – first parameter retrieved (default: `'X'`)

- **val2** – second parameter retrieved (default: `'Y'`)

- **vals** – additional parameters to retrieve (optional)
