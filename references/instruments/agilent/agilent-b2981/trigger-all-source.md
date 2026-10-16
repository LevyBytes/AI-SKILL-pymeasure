# pymeasure.instruments.agilent.AgilentB2981.trigger_all_source

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger_all_source*: Any*

Select the trigger source for action ‘ALL’.

Type:

str; accepted values are exactly `AINT`, `BUS`, `TIM`, `INT1`, `INT2`, `LAN`, `TIN`, `EXT1` to `EXT7`

- `AINT` lets internal algorithms choose the trigger source best matched to the present operating mode.

- `BUS` uses a remote-interface trigger command, including the group execute trigger (GET) and the TRG command.

- `TIM` uses an internally generated signal at each interval set by `trigger_all_timer`.

- `INT1` and `INT2` use a signal from internal bus 1 or 2.

- `LAN` uses the LXI trigger identified by `trigger_all_source_lan_id`.

- `EXT1` to `EXT7` uses GPIO pin n on the rear-panel Digital I/O D-sub connector as an input port. n = 1 to 7.

- `TIN` uses the BNC Trigger In.
