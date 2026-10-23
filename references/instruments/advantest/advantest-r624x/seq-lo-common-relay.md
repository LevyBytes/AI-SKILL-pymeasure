# pymeasure.instruments.advantest.advantestR624X.seq_lo_common_relay

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_lo_common_relay(*enable*, *lo_relay=None*)

Create the command string for LTL (LO common connection relay).

Parameters:

- **enable** (*bool*): Turn the connection relay on.

- **lo_relay** (*bool** or **None*): Enable the internal analog common relay; None leaves it unchanged. (default: `None`)

Return type:

str
