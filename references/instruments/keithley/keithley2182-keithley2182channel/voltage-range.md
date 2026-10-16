# pymeasure.instruments.keithley.keithley2182.Keithley2182Channel.voltage_range

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *voltage_range*: Any*

Set the positive full-scale voltage range in Volts. Keithley 2182 range selection is based on the expected voltage. DCV1 offers 10 mV, 100 mV, 1 V, 10 V, and 100 V across five ranges. DCV2 offers 100 mV, 1 V, and 10 V across three ranges. Limits are 0 to 120 V on Ch. 1 and 0 to 12 V on Ch. 2. Setting this property turns off auto-range automatically.(dynamic)
