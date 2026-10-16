# pymeasure.instruments.hp.HP437B.duty_cycle

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *duty_cycle

Controls the duty cycle used to compute a pulsed input signal. With this function, the power meter reports pulse power for a rectangular pulsed input signal. Valid `duty_cycle` values run from 0.00001 to 0.99999.

The pulse power reported by the power meter is calculated mathematically, not directly measured. The meter measures the pulsed input signal's average power, then divides that reading by the duty cycle value to produce pulse power.
