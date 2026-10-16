# pymeasure.adapters.PrologixAdapter.eos

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *eos

Control GPIB termination characters (str).

possible values:

- CR+LF

- CR

- LF

- empty string

On host input, unescaped LF, CR, and ESC characters are stripped, then the GPIB terminators specified by this command are appended before data is sent to instruments. This command does not change data received from instruments over GPIB port.
