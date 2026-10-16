# pymeasure.instruments.mksinst.mks974b.MKS974B

*class *pymeasure.instruments.mksinst.mks974b.MKS974B(*adapter*, *name='MKS 974B vacuum pressure transducer'*, *address=253*, ***kwargs*)

Bases: [`MKSInstrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mksinst.html#pymeasure.instruments.mksinst.mksinst.MKSInstrument)

MKS 974B vacuum pressure transducer

The device connection uses an RS232/RS485 serial link.

The 974B pressure transducer combines cold cathode ionization current measurement, a Pirani sensor, and a Piezo sensor, allowing one pressure gauge to span a wide pressure range. Optional hardware may include up to three mechanical relays that energize from the measured pressure value.

Parameters:

- **adapter** – pyvisa resource name for the instrument, or an adapter instance

- **name** (*string*) – Instrument name.

- **address** – address inserted into each device message (default=253) (default: `253`)

- **kwargs** – Any key-word argument accepted by `Instrument`
