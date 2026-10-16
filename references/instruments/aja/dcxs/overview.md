# pymeasure.instruments.aja.DCXS

Scope includes AJA DCXS-750 or 1500 DC magnetron sputtering power supply; vendor AJA International; instrument Ametek 7270 DSP Lockin Amplifier; vendor Ametek; vendor F.W. Bell; instrument F.W. Bell 5080 Handheld Gaussmeter; device Toptica IBeam Smart Laser diode; vendor Toptica; controller ESP 300 Motion Controller; vendor Newport.

## AJA DCXS-750 or 1500 DC magnetron sputtering power supply

### AJA DCXS-750 or 1500 DC magnetron sputtering power supply

 *class *pymeasure.instruments.aja.DCXS(*adapter*, *name='AJA DCXS sputtering power supply'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Reference for AJA DCXS-750 / 1500 hardware. This DC magnetron sputtering power supply exposes multiple outputs.

Communicate with the device over an RS232 serial connection. Its fixed communication settings are 38400, one stopbit, no parity. Protocol traffic uses one-character commands and fixed length replies, with no terminator on either side.

Parameters:

- **adapter** – pyvisa resource name for the instrument, or an adapter instance

- **name** (*string*) – Instrument name.

- **kwargs** – Any key-word argument accepted by Instrument
