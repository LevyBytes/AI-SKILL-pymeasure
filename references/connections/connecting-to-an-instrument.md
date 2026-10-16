# Connecting to an instrument

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
