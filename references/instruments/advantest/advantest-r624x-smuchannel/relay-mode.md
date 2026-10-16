# pymeasure.instruments.advantest.advantestR624X.SMUChannel.relay_mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *relay_mode*: Any*

Configure HI/LO relay behavior for standby mode (`OPM`).

Type:

int

1. Mode where the HI side alone turns ON during execution, while standby turns both HI and LO OFF.

2. Mode where the LO side alone turns ON during execution, while standby turns both HI and LO OFF.

3. Mode where HI and LO both turn ON during execution, while standby turns both HI and LO OFF.

4. Mode where the HI side alone turns ON during execution, while standby turns only the HI side OFF.
