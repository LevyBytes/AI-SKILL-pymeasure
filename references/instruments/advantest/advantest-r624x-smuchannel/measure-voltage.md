# pymeasure.instruments.advantest.advantestR624X.SMUChannel.measure_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_voltage(*enable=True*, *internal_measurement=True*, *voltage_range=VoltageRange.AUTO*)

Configure voltage measurement ON/OFF, measurement input, and voltage measurement range (`RV`).

Parameters:

- **enable** (*bool**, **optional*) – Boolean setting that turns voltage measurement on or off. True measures voltage at the OUTPUT terminal; False measures voltage from rear-panel -ANALOG COMMON. (default: `True`)

- **internal_measurement** (*bool**, **optional*) – Boolean setting for enabling or disabling internal measurement. (default: `True`)

- **voltage_range** (`VoltageRange`, optional) – Specifying voltage range (default: `<VoltageRange.AUTO: 0>`)
