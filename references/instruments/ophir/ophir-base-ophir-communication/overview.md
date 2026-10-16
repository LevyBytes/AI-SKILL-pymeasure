# pymeasure.instruments.ophir.ophir_base.OphirCommunication

*class *pymeasure.instruments.ophir.ophir_base.OphirCommunication(*adapter*, *name='Ophir'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Base class for serial communication with Ophir devices; it does not define properties.

Communication uses ASCII and works with RS-232 and USB connections.

For USB, a COM (win32) object is also available as another option instead of this driver.
