# pymeasure.instruments.agilent.AgilentB2981.arm_acquisition_source

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *arm_acquisition_source*: Any*

Select the arm trigger source for action ‘ACQuire’.

Type:

str; accepted values are exactly `AINT`, `BUS`, `TIM`, `INT1`, `INT2`, `LAN`, `TIN`, `EXT1` to `EXT7`

- `AINT` lets internal algorithms choose the arm source best matched to the present operating mode.

- `BUS` uses a remote-interface trigger command, including the group execute trigger (GET) and the TRG command.

- `TIM` uses an internally produced signal at the interval configured by the arm_timer command.

- `INT1` and `INT2` use a signal from internal bus 1 or 2.

- `LAN` uses the LXI trigger identified by the arm_source_lan_id command.

- `EXT1` to `EXT7` uses GPIO pin n on the rear-panel Digital I/O D-sub connector as an input port. n = 1 to 7.

- `TIN` uses the BNC Trigger In.
