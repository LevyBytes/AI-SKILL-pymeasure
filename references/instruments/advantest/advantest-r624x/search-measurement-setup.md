# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.search_measurement_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

search_measurement_setup(*search_mode*, *occurrence_after_stop*, *command*)

Configure search measurement sense/search channel parameters (`MAR~;NENT`).

Parameters:

- **search_mode** (int or `SearchMode`) – Search mode indicating binary/linear behavior and the sense/search channel.

- **occurrence_after_stop** (int or `OccurrenceAfterStop`) – Output behavior used after stopping.

- **command** (*str*) – Inner command string (e.g. `'FXV 1,20,6,17,2,0'`). Valid prefixes: FXV, FXI, PXV, PXI, WV, WI, PWV, PWI, CMD.

Note

Inside a search context, the same inner command string uses search-specific parameter meanings. Consult the instrument manual for the reinterpretation rules applied to FXV/FXI/PXV/PXI and WV/WI/PWV/PWI.
