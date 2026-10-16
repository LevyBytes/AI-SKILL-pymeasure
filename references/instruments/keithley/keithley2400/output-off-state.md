# pymeasure.instruments.keithley.Keithley2400.output_off_state

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *output_off_state*: Any*

Control the output-off state.

str:

- ?disconnected?: Opens the output relay; avoid this state for frequent output on/off cycling to limit relay wear.

- ?normal?: Selects the V-source and sets it to 0V.

- ?zero?: Lets the sourcemeter measure current while the output is off.

- ?guard?: Selects the I-source and sets it to 0A.

Deprecated since version 0.16: Do not use ?HIMP?, ?NORM?, ?ZERO?, or ?GUAR? with `output_off_state`.
