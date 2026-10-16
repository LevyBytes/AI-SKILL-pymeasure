# pymeasure.adapters.PrologixAdapter

*class *pymeasure.adapters.PrologixAdapter(*resource_name*, *address=None*, *auto=False*, *eoi=True*, *eos='\n'*, *gpib_read_timeout=None*, ***kwargs*)

Bases: `VISAAdapter`

Wraps the extra commands required for a Prologix GPIB-USB Adapter while communicating through `VISAAdapter`.

A PrologixAdapter is built from the Prologix-device connection plus the instrument's GPIB address. To share the connection, call `gpib()` to create additional PrologixAdapters for other GPIB addresses.

Parameters:

- **resource_name** – Connection target for the Prologix hardware, given as a [VISA resource string](https://pyvisa.readthedocs.io/en/latest/introduction/names.html); example: “ASRL5” for COM port 5.

- **address** – Integer GPIB address for the target instrument. (default: `None`)

- **auto** – Turn read-after-write on or off and address the instrument to listen. (default: `False`)

- **eoi** – Turn EOI assertion on or off. (default: `True`)

- **eos** – Command termination string to set (CR+LF, CR, LF, or “”) (default: `'\\n'`)

- **gpib_read_timeout** – GPIB read timeout in milliseconds, from 1..3000 (default: `None`)

- **kwargs** – Extra key-word arguments used when constructing a new serial object

Variables:

**address** – Integer GPIB address for the target instrument.

Usage example:

```python
from pymeasure.instruments.keithley.keithley2000 import Keithley2000
from pymeasure.instruments.keithley.keithley2400 import Keithley2400
from pymeasure.adapters.prologix import PrologixAdapter

adapter = PrologixAdapter("ASRL5::INSTR", 7)
sourcemeter = Keithley2400(adapter)  # at GPIB address 7
# generate another instance with a different GPIB address:
adapter2 = adapter.gpib(9)
multimeter = Keithley2000(adapter2)  # at GPIB address 9

```

For Linux user access to the Prologix adapter, create `/etc/udev/rules.d/51-prologix.rules` containing:

```text
SUBSYSTEMS=="usb",ATTRS{idVendor}=="0403",ATTRS{idProduct}=="6001",MODE="0666"

```

Reload the udev rules afterwards with:

```bash
sudo udevadm control --reload-rules
sudo udevadm trigger

```

Because the Prologix adapter uses one USB CDC channel for both adapter commands and GPIB traffic, keep these constraints in mind:

- For GPIB reads, call the normal `read()` method.

- Reads that target the Prologix device's own responses should pass `prologix=True` to `read()` so no GPIB read is requested. The same parameter is needed in “listen-only” mode, where GPIB traffic is forwarded automatically.

- Send binary bus data with `write_binary_values()` so bytes that the Prologix adapter might parse as commands are escaped correctly. The default behavior of `write_binary_values()` assumes floating-point binary data and prepends IEEE headers; for plain bytes, adjust `datatype` and `header_fmt`:

```python
multimeter.write_binary_values('W', [addr], datatype='B', header_fmt='empty')

```
