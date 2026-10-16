# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.set_lo_common_connection_relay

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_lo_common_connection_relay(*enable*, *lo_relay=None*)

Set up the `LTL` LO common relay connection linking channels A and B.

Parameters:

- **enable** (*bool*) – Boolean property controlling whether the connection relay is enabled. Valid values are True and False.

- **lo_relay** (*bool**, **optional*) – Boolean setting for enabling the internal analog common relay. Use True, False, or None (don’t change lo relay setting). (default: `None`)
