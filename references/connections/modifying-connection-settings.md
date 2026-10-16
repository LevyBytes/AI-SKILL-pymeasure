# Modifying connection settings

At times, communication with a device requires connection settings to be adjusted. Reasons include a non-standard device, a non-standard connection, or troubleshooting a device that does not reply.

Connecting with a string or integer causes PyMeasure to use a [`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter) internally. Pass additional settings as keyword arguments. For example, when connecting to the Keithely2400 as above, use this form to set a fast baud rate on a quick connection:

```python
from pymeasure.instruments.keithley.keithley2400 import Keithley2400

sourcemeter = Keithley2400("ASRL2", timeout=500, baud_rate=115200)

```

These keyword arguments override defaults that the instrument may define, including generally valid settings such as `timeout` and interface-specific settings such as `baud_rate`.

A misspelled argument, or one that is not valid for the chosen interface, raises an exception.

With a separately-created Adapter instance, set custom options during adapter creation. Keyword arguments passed later are ignored.

---

The examples above show multiple ways to communicate with instruments while adapters keep instrument code separate from communication protocols. The next topic covers methods for setting up measurements.
