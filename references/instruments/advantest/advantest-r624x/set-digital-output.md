# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.set_digital_output

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_digital_output(*values*)

Send a 16-bit signal from the rear-panel DIGITAL OUT output terminal (`DIOS`). When multiple values are supplied, output them about every 2ms and keep the last value fixed as final data.

Parameters:

**values** (*int** or **list*) – Bit values for digital out

Note

Digital data reaches the DIGITAL OUT pin only for bits selected by the DIOE command. Unselected bits become alarm output or unused bits, so no digital data is produced for them.
