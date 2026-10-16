# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.sequence_program_number

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *sequence_program_number*: Any*

Query how many program sequences are stored in sequence memory (`LNUB?`).

Responses start with `#3XXX,line1,line2,...`; `XXX` is the 3-digit stored-program count, followed by line numbers. This property exposes only the integer count.
