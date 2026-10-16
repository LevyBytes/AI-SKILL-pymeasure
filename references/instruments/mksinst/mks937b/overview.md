# pymeasure.instruments.mksinst.mks937b.MKS937B

*class *pymeasure.instruments.mksinst.mks937b.MKS937B(*adapter*, *name='MKS 937B vacuum gauge controller'*, *address=253*, ***kwargs*)

Bases: [`MKSInstrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mksinst.html#pymeasure.instruments.mksinst.mksinst.MKSInstrument)

MKS 937B vacuum gauge controller

The device connection uses an RS232/RS485 serial link.

The 937B gauge controller accepts as many as 6 pressure measurement channels for different gauge types, including ionization gauges, Pirani and piezo gauges. Its twelve setpoint relays can energize at configured pressure readings. Relay-to-channel mapping is fixed: each pressure channel owns two relays.

Parameters:

- **adapter** – pyvisa resource name for the instrument, or an adapter instance

- **name** (*string*) – Instrument name.

- **address** – address inserted into each device message (default=253) (default: `253`)

- **kwargs** – Any key-word argument accepted by Instrument
