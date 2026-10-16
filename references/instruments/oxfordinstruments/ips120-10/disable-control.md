# pymeasure.instruments.oxfordinstruments.IPS120_10.disable_control

[Owning PyMeasure class, adapter and connection contract](overview.md)

disable_control()

When the field is at 0T, disables IPS active control by switching off the switch heater, clamping the output, and placing control in local mode. If the field is not at 0T, raises `MagnetError`.
