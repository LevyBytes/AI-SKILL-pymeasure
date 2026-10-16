# pymeasure.instruments.advantest.advantestR624X.SESR

*class *pymeasure.instruments.advantest.advantestR624X.SESR(**values*)

Bases: `IntFlag`

Standard Event Status Register (SESR) bit assigment:

| Bit (dec) | Description |
| --- | --- |
| 0 | OPC (Operation Complete) not used |
| 1 | RQC unused |
| 2 | QYE (Query Error) is set if the output queue overflows, or if a read is attempted without output data. |
| 3 | DDE (Device Dependent Error) is set when the self-test reports an error. |
| 4 | EXE (Execution Error) is set when input data falls outside the internally configured range, or when the command is not executable. |
| 5 | CME (Command Error) is set for an undefined header, an invalid data format, or command syntax error. |
| 6 | URQ unused |
| 7 | PON is set after power changes from OFF to ON. |
