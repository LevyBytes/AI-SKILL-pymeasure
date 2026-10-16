# pymeasure.instruments.oxfordinstruments.mercuryitc.Heater

*class *pymeasure.instruments.oxfordinstruments.mercuryitc.Heater(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Heater channel for the Oxford Instruments Mercury iTC.

The heater output exposes several parameters, and some properties are configurable. PID control is handled through an associated temperature sensor. The heater is assumed to already be linked to a temperature sensor control loop, or else configured for open-loop operation.
