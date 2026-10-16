# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.error_register

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *error_register*: Any*

Read the error register contents as a 5-digit integer (`ERR?`).

The response uses `UUEEN`: `UU` gives the unit number (00=system, 01=ch A, 02=ch B) and `EEN` gives the error code. Use `check_errors()` to perform structured error checking with messages.
