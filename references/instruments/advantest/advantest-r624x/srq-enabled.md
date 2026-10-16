# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.srq_enabled

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *srq_enabled*: Any*

Enable or disable the GPIB SRQ feature with a bool (`S0/S1`).

Type:

bool

The SRQ feature on the GPIB bus supplies hardware handshaking between the instrument and the PC's GPIB controller card. It lets data transfers to the PC be synchronized with instrument state without relying on time delay functions.
