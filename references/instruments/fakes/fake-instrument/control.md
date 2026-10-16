# pymeasure.instruments.fakes.FakeInstrument.control

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *control(*get_command*, *set_command*, *docs*, *validator=<function FakeInstrument.&lt;lambda&gt;>*, *values=()*, *map_values=False*, *get_process=<function FakeInstrument.&lt;lambda&gt;>*, *set_process=<function FakeInstrument.&lt;lambda&gt;>*, *check_set_errors=False*, *check_get_errors=False*, ***kwargs*)

Fake Instrument.control.

Remove command text, then store and return only the values selected by format strings, emulating many simple commands. This matches the handling used by tests in test_instrument.
