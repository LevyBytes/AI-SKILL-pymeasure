# Connecting

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Connecting to an instrument

Once the [Quick Start](https://pymeasure.readthedocs.io/en/latest/quick_start.html) section is complete, PyMeasure should be installed and ready to use. This part explains how to connect to an instrument, with a Keithley 2400 SourceMeter serving as the example. Work through the tutorial from a command prompt, IPython terminal, or Jupyter notebook.

Start by importing the instrument you want to use.

```python
from pymeasure.instruments.keithley import Keithley2400

```

Next, create the object and supply the VISA address. In this example, the instrument is reached over GPIB (using VISA) at address 4:

```python
sourcemeter = Keithley2400("GPIB::4")

```

Note

The normal way to create pymeasure instruments is to pass the right resource string. The adapters section below gives additional detail.

When the resource string for identifying the instrument is uncertain, call `pymeasure.instruments.resources.list_resources()` to list all available resources:

```python
from pymeasure.instruments.resources import list_resources
list_resources()

```

When the USB properties (vendor id, product id, serial numer) are known for the serial device, you can query for the VISA resource string:

```python
from pymeasure.instruments import find_serial_port
resource_name = find_serial_port(vendor_id=15, product_id=0x12e5, serial_number="sn56X")

```

For instruments that implement standard SCPI commands, the `id` property returns the result from the `*IDN?` SCPI command and identifies the instrument.

```python
sourcemeter.id

```

That matches a direct manual call to the SCPI command.

```python
sourcemeter.ask("*IDN?")

```

In this case, the `ask` method sends the SCPI command, reads the result, and returns it. Calling the methods below is equivalent as well.

```python
sourcemeter.write("*IDN?")
sourcemeter.read()

```

This shows that top-level methods such as `id` are assembled from multiple lower-level methods. Use either level according to the operation you need. PyMeasure keeps those lower-level details out of the way so the main workflow stays in focus.

Instruments can also be used inside a `with` statement.

```python
with Keithley2400("GPIB::4") as sourcemeter:
    sourcemeter.id

```

Exiting the `with`-block calls the instrument's `shutdown` method, which places the system in a safe state.

```python
with Keithley2400("GPIB::4") as sourcemeter:
    sourcemeter.isShutdown == False
sourcemeter.isShutdown == True

```

### Using adapters

Adapters handle communication with the hardware underneath. In the earlier example, constructing the instrument with the string GPIB::4 creates a VISAAdapter by default, the most common default adapter, and connects through VISA. Supplying a string (or, for GPIB, an integer) is the overwhelmingly common pattern for creating pymeasure instruments.

For cases outside the standard setup, you can pass an adapter object rather than passing a string.

```python
from pymeasure.adapters import VISAAdapter

adapter = VISAAdapter("GPIB::4")
sourcemeter = Keithely2400(adapter)

```

To use a Prologix GPIB device on `/dev/ttyUSB0` instead, build the adapter in the same general manner; Linux requires the proper permissions, as noted for [`PrologixAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.PrologixAdapter). Many instruments can share one Prologix adapter. Because of that, an existing instance can be used to generate new [`PrologixAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.PrologixAdapter) instances for different GPIB addresses.

```python
from pymeasure.adapters import PrologixAdapter

adapter = PrologixAdapter('ASRL/dev/ttyUSB0::INSTR', address=7)
sourcemeter = Keithley2400(adapter)  # at GPIB address 7
multimeter = Keithley2000(adapter.gpib(9))  # at GPIB address 9

```

### Modifying connection settings

At times, communication with a device requires connection settings to be adjusted. Reasons include a non-standard device, a non-standard connection, or troubleshooting a device that does not reply.

Connecting with a string or integer causes PyMeasure to use a [`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter) internally. Pass additional settings as keyword arguments. For example, when connecting to the Keithely2400 as above, use this form to set a fast baud rate on a quick connection:

```python
sourcemeter = Keithley2400("ASRL2", timeout=500, baud_rate=115200)

```

These keyword arguments override defaults that the instrument may define, including generally valid settings such as `timeout` and interface-specific settings such as `baud_rate`.

A misspelled argument, or one that is not valid for the chosen interface, raises an exception.

With a separately-created Adapter instance, set custom options during adapter creation. Keyword arguments passed later are ignored.

---

The examples above show multiple ways to communicate with instruments while adapters keep instrument code separate from communication protocols. The next topic covers methods for setting up measurements.
