# pymeasure.instruments.advantest.advantestR624X.SMUChannel.set_wire_mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_wire_mode(*four_wire*, *lo_guard=True*)

Configure remote sense and the LO-GUARD relay ON/OFF (`OSL`).

Parameters:

- **four_wire** (*bool*) – Boolean setting for four wire measurements. True enables 4-wire sensing; False enables two-terminal sensing.

- **lo_guard** (*bool*) – Boolean setting that enables or disables the LO-GUARD relay.
