# pymeasure.instruments.mksinst.mksinst.RelayChannel

*class *pymeasure.instruments.mksinst.mksinst.RelayChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Configuration for the optional setpoint relay.

Depending on `direction`, the relay energizes either below or above the setpoint. Crossing the reset value in the opposite direction de-energizes it.

By default, the device applies auto hysteresis equal to 10% of the setpoint value; any change to the setpoint value or direction overwrites the current reset value. To use a hysteresis other than 10%, configure the setpoint value and direction first, then set the reset value.
