# pymeasure.adapters.VISAAdapter

*class *pymeasure.adapters.VISAAdapter(*resource_name*, *visa_library=''*, *log=None*, ***kwargs*)

Bases: `Adapter`

Adapter for the VISA library that communicates with instruments through PyVISA.

This is the library's main adapter and is used by most instruments.

Parameters:

- **resource_name** (`Union`[`ProtocolAdapter`, `VISAAdapter`, `int`, `str`]) – A [VISA resource string](https://pyvisa.readthedocs.io/en/latest/introduction/names.html) or integer GPIB address identifying the connection target

- **visa_library** (`str`) – PyVISA VisaLibrary Instance, VISA library path, or VisaLibrary spec string (`@py` or `@ivi`); when omitted, the platform default is selected. (default: `''`)

- **log** (`Optional`[`Logger`]) – Logger to use as the parent for the ‘Adapter’ logger. (default: `None`)

- ****kwargs** – Keyword arguments used to configure the PyVISA connection.

Kwargs:

PyVISA creates the connection, and keyword arguments configure it. The valid set varies with the interface selected by the current `resource_name`, such as serial, GPIB, TCPI/IP, or USB.

The adapter uses a flexible scheme for interface-specific *default values* while still letting the instrument user *override any setting* when needed.

When a kwarg is named for a pyVISA interface type, commonly `asrl`, `gpib`, `tcpip`, or `usb`, its value is a dictionary of defaults for that interface. Example: `asrl={'baud_rate': 4200}`.

Other kwargs either apply generally, such as `timeout=500`, or take precedence over interface-specific defaults. For instance, with resource name `ASRL1`, `baud_rate=115200` replaces an `asrl` default of 4200.

For user-side connection adjustments, see [Modifying connection settings](https://pymeasure.readthedocs.io/en/latest/tutorial/connecting.html#connection-settings). For instrument implementation defaults, see [Defining default connection settings](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#default-connection-settings).
