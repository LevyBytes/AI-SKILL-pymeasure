# pymeasure.instruments.hcp.TC038

*class *pymeasure.instruments.hcp.TC038(*adapter*, *name='TC038'*, *address=1*, *timeout=1000*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Communication support for the HCP TC038 oven.

This older version uses an AC power supply and AC heater.

Parity or framing errors occur from time to time, so the application must handle them.

For every valid request or command, the oven responds with "OK".

Parameters:

- **adapter** (`Union`[[`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter), `int`, `str`]) - COM-Port name.

- **name** (`str`) - Instrument name. (default: `'TC038'`)

- **address** (`int`) - Device address; should be between 1 and 99. (default: `1`)

- **timeout** (`int`) - Timeout in ms. (default: `1000`)

- **kwargs** - Extra arguments passed to the Instrument base class.
