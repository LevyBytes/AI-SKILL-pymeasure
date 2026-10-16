# pymeasure.instruments.racal.Racal1992.write

[Owning PyMeasure class, adapter and connection contract](overview.md)

write(*command*, ***kwargs*)

Prefix every command sent to the instrument with a space to work around an unusual model issue.

Almost every device should work without it, but using it is harmless; it also fixes a real issue seen on a few devices.
