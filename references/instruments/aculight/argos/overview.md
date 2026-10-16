# pymeasure.instruments.aculight.argos.Argos

*class *pymeasure.instruments.aculight.argos.Argos(*adapter*, *name='Argos 2400 OPO system'*, *query_delay=0.01*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Communication model for the Aculight Argos 2400 OPO system.

The device returns only the full value set at once, which takes around 100 ms. When more than one value is needed, read the `state` property rather than separate properties. Any property read reads all properties, then returns the matching value.

Also note that block temperature cannot be set remotely; use the front panel.

Cable type: RS232 null modem female DB9 connectors. Pins 2 and 3 must cross between the two sides. Pin2 is RX, Pin3 is Tx, and Pin 5 is ground.

Parameters:

- **adapter** – resource name

- **query_delay** - Delay in seconds between write and read. (default: `0.01`)
