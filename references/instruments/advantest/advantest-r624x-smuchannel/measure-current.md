# pymeasure.instruments.advantest.advantestR624X.SMUChannel.measure_current

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_current(*enable=True*, *internal_measurement=True*, *current_range=CurrentRange.AUTO*)

Configure current measurement ON/OFF, measurement input, and current measurement range (`RI`).

Parameters:

- **enable** (*bool**, **optional*) – Boolean setting that turns current measurement on or off. True measures current at the OUTPUT terminal; False measures current from rear-panel -ANALOG COMMON. (default: `True`)

- **internal_measurement** (*bool**, **optional*) – Boolean setting for enabling or disabling internal measurement. (default: `True`)

- **current_range** (`CurrentRange`, optional) – Specifying current range. (default: `<CurrentRange.AUTO: 0>`)

Warning

`CurrentRange.AUTO` and `AUTO_*` ranges are invalid when the channel is set for pulse measurement or pulse sweep and will produce error 00211. For pulsed modes, select a fixed range such as `CurrentRange.FIXED_BEST`.
