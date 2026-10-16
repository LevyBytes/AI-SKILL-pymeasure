# pymeasure.instruments.tcpowerconversion.CXN

Covers: T&C Power Conversion AG Series Plasma Generator CXN; T&C Power Conversion.

## T&C Power Conversion AG Series Plasma Generator CXN

### T&C Power Conversion AG Series Plasma Generator CXN

 *class *pymeasure.instruments.tcpowerconversion.CXN(*adapter*, *name='T&C RF sputtering power supply'*, *address=0*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

The AG Series Plasma Generator CXN from T&C Power Conversion also appears under AJA International Inc branding as 0113 GTC or 0313 GTC.

Connect to the device over an RS232 serial connection. Its fixed communication settings are 38400, stopbit one, parity none. The device uses command/response communication: each received command is acknowledged by returning '*'. If the device does not recognize the command, it returns '?'.

Command message bytes (B) are arranged as: header: 1B, always 'C'; address: 1B, ignored; command id: 2B; parameter 1: 2B; parameter: 2B; checksum: 2B.

Response message bytes are arranged as: header: 1B, always 'R'; device address: 1B; data package length: 2B; data: variable length; checksum: 2B. Response messages arrive after the acknowledge byte.

Parameters:

- **adapter** - pyvisa resource name for the instrument, or an adapter instance

- **name** (*string*) - Name assigned to the instrument.

- **kwargs** - Any valid Instrument key-word argument

Note

To enable parameter setting, request control and periodically poll any device value, at least once per 2s. Otherwise control is lost and the device resets certain parameters, such as setpoint and disable RF. If no value needs polling but control should stay active, use the ping method.
