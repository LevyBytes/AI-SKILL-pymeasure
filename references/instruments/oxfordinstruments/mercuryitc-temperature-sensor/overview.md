# pymeasure.instruments.oxfordinstruments.mercuryitc.TemperatureSensor

*class *pymeasure.instruments.oxfordinstruments.mercuryitc.TemperatureSensor(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Temperature sensor channel for the Oxford Instruments Mercury iTC.

Because validity depends on sensor type, such as diode or NTC/PTC resistor, some properties may not apply. Sensor configuration therefore has to be known and configured a priori. Currently, only diode sensor types are implemented.

Loop control is grouped with temperature sensor properties because control loops are reached through temperature sensors rather than through heaters.
