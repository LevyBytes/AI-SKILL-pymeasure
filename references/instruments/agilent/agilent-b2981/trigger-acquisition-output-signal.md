# pymeasure.instruments.agilent.AgilentB2981.trigger_acquisition_output_signal

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger_acquisition_output_signal*: Any*

Select the trigger signal output for action ‘ACQuire’.

Type:

str; accepted values are exactly `INT1`, `INT2`, `LAN`, `TOUT`, `EXT1` to `EXT7`

- `INT1` and `INT2` choose internal bus 1 or 2.

- `LAN` selects a LAN port.

- `EXT1` to `EXT7` chooses GPIO pin n on the rear-panel Digital I/O D-sub connector as an output port. n = 1 to 7.

- `TOUT`: chooses the BNC Trigger Out.

Applies to the transition between the idle state and the trigger layer.
