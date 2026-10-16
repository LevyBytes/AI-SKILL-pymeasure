# pymeasure.instruments.hp.HP437B.trigger_immediate

[Owning PyMeasure class, adapter and connection contract](overview.md)

trigger_immediate()

Trigger immediate.

On receiving the trigger immediate program code, the power meter adds one more data point to the digital filter, measures the filter reading, and updates the display plus HP-IB. Executing trigger immediate does not clear the internal digital filter. The meter then waits until the controller reads the measurement results. During that wait, most bus commands can be handled without losing the results. If a trigger immediate command is followed by GET (Group Execute Trigger), the trigger immediate command is canceled and a fresh measurement cycle runs. After results are read onto the bus, the meter always returns to standby/hold mode. Measurements from trigger immediate are normally valid only when the power meter is steady and settled.
