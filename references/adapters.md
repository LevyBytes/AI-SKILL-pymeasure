# Adapters (part 1)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### pymeasure.adapters

Adapters decouple instrument classes from the transport used to reach hardware. The instrument side handles protocol-specific behavior (see [protocol guidance](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/advanced_communication.html#advanced-communication-protocols)); the adapter manages traffic over the device connection. In common use, the caller gives the instrument only a connection string or integer (see [connection guide](https://pymeasure.readthedocs.io/en/latest/tutorial/connecting.html#connecting-to-an-instrument)); internally that route selects `pymeasure.adapters.VISAAdapter`.

### Adapter base class

 *class *pymeasure.adapters.Adapter(*log=None*, ***kwargs*)

Superclass for Adapter child classes that bridge the Instrument object and its connection, allowing multiple communication techniques.

Use this class solely as a superclass.

Parameters:

-

**log** (`Optional`[`Logger`]) – Logger to use as the parent for the ‘Adapter’ logger. (default: `None`)

-

****kwargs** – Extra keyword arguments accepted for cooperative initialization.

 close()

Close the connection.

Return type:

`None`

 connection*: `ConnectionProtocol`*

 flush_read_buffer()

Clear and drop all input-buffer data. Subclasses must provide the implementation.

Return type:

`None`

 read(***kwargs*)

Read until read_termination without including it, or consume the full read buffer.

Subclass implementations must not replace this method.

Parameters:

****kwargs** – Keyword arguments forwarded to the underlying connection.

Returns str:

Instrument reply decoded as ASCII, with read_termination omitted.

Return type:

`str`

 read_binary_values(*header_bytes=0*, *termination_bytes=None*, *dtype=<class 'numpy.float32'>*, *sep=''*, ***kwargs*)

Produces a numpy array from the response to a binary-data query.

Parameters:

-

**header_bytes** (*int*) – Byte count at the message header to skip.

-

**termination_bytes** (*int*) – Byte count to remove from the message tail, or None.

-

**dtype** – NumPy dtype used when formatting the resulting values. (default: `<class 'numpy.float32'>`)

-

**sep** (*string*) – Character separator; when provided, fromstring is used, otherwise frombytes is used.

-

****kwargs** – Additional parameters supplied to the NumPy fromstring / frombytes method.

Returns:

NumPy array of values

Raises:

**ValueError** – raised when the data buffer is empty or malformed

 read_bytes(*count=-1*, *break_on_termchar=False*, ***kwargs*)

Read the requested byte count from the instrument.

Subclass implementations must not replace this method.

Parameters:

-

**count** (*int*) – Bytes requested for the read; -1 means use the complete read buffer.

-

**break_on_termchar** (*bool*) – Stop the read when a termination character is encountered.

-

****kwargs** – Keyword arguments forwarded to the underlying connection.

Returns bytes:

Instrument byte response, including the termination bytes.

Return type:

`bytes`

 write(*command*, ***kwargs*)

Send a string command to the instrument with write_termination appended.

Subclass implementations must not replace this method.

Parameters:

-

**command** (*str*) – Command string sent to the instrument, excluding termination.

-

****kwargs** – Keyword arguments forwarded to the underlying connection.

Return type:

`None`

 write_binary_values(*command*, *values*, *termination=''*, ***kwargs*)

Send binary data to the instrument, such as a waveform for signal generators.

Parameters:

-

**command** (`str`) – command string sent to the instrument

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – iterable containing the binary values

-

**termination** (`str`) – String appended after the payload to end the message. (default: `''`)

-

****kwargs** – Key-word arguments forwarded to `Adapter._format_binary_values()`

Returns:

`int` – number of bytes written

 write_bytes(*content*, ***kwargs*)

Send raw bytes content to the instrument.

Subclass implementations must not replace this method.

Parameters:

-

**content** (*bytes*) – Bytes content sent to the instrument.

-

****kwargs** – Keyword arguments forwarded to the underlying connection.

Return type:

`None`

### VISA adapter

 *class *pymeasure.adapters.VISAAdapter(*resource_name*, *visa_library=''*, *log=None*, ***kwargs*)

Bases: `Adapter`

Adapter for the VISA library that communicates with instruments through PyVISA.

This is the library's main adapter and is used by most instruments.

Parameters:

-

**resource_name** (`Union`[`ProtocolAdapter`, `VISAAdapter`, `int`, `str`]) – A [VISA resource string](https://pyvisa.readthedocs.io/en/latest/introduction/names.html) or integer GPIB address identifying the connection target

-

**visa_library** (`str`) – PyVISA VisaLibrary Instance, VISA library path, or VisaLibrary spec string (`@py` or `@ivi`); when omitted, the platform default is selected. (default: `''`)

-

**log** (`Optional`[`Logger`]) – Logger to use as the parent for the ‘Adapter’ logger. (default: `None`)

-

****kwargs** – Keyword arguments used to configure the PyVISA connection.

Kwargs:

PyVISA creates the connection, and keyword arguments configure it. The valid set varies with the interface selected by the current `resource_name`, such as serial, GPIB, TCPI/IP, or USB.

The adapter uses a flexible scheme for interface-specific *default values* while still letting the instrument user *override any setting* when needed.

When a kwarg is named for a pyVISA interface type, commonly `asrl`, `gpib`, `tcpip`, or `usb`, its value is a dictionary of defaults for that interface. Example: `asrl={'baud_rate': 4200}`.

Other kwargs either apply generally, such as `timeout=500`, or take precedence over interface-specific defaults. For instance, with resource name `ASRL1`, `baud_rate=115200` replaces an `asrl` default of 4200.

For user-side connection adjustments, see [Modifying connection settings](https://pymeasure.readthedocs.io/en/latest/tutorial/connecting.html#connection-settings). For instrument implementation defaults, see [Defining default connection settings](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#default-connection-settings).

 close()

Close the connection. :rtype: `None`

Note

Close the resource connection for every adapter currently sharing it, such as adapters on one GPIB line.

 connection*: `Union`[`ProtocolAdapter`, `MessageBasedResource`]*

 flush_read_buffer()

Clear and drop the input buffer.

Following pyvisa behavior, the read and receive buffers are discarded. If the read buffer contained data without an END-indicator, the device is read until an END indicator appears, which drops that data.

Return type:

`None`

 read(***kwargs*)

Read until read_termination without including it, or consume the full read buffer.

Subclass implementations must not replace this method.

Parameters:

****kwargs** – Keyword arguments forwarded to the underlying connection.

Returns str:

Instrument reply decoded as ASCII, with read_termination omitted.

Return type:

`str`

 read_binary_values(*header_bytes=0*, *termination_bytes=None*, *dtype=<class 'numpy.float32'>*, *sep=''*, ***kwargs*)

Produces a numpy array from the response to a binary-data query.

Parameters:

-

**header_bytes** (*int*) – Byte count at the message header to skip.

-

**termination_bytes** (*int*) – Byte count to remove from the message tail, or None.

-

**dtype** – NumPy dtype used when formatting the resulting values. (default: `<class 'numpy.float32'>`)

-

**sep** (*string*) – Character separator; when provided, fromstring is used, otherwise frombytes is used.

-

****kwargs** – Additional parameters supplied to the NumPy fromstring / frombytes method.

Returns:

NumPy array of values

Raises:

**ValueError** – raised when the data buffer is empty or malformed

 read_bytes(*count=-1*, *break_on_termchar=False*, ***kwargs*)

Read the requested byte count from the instrument.

Subclass implementations must not replace this method.

Parameters:

-

**count** (*int*) – Bytes requested for the read; -1 means use the complete read buffer.

-

**break_on_termchar** (*bool*) – Stop the read when a termination character is encountered.

-

****kwargs** – Keyword arguments forwarded to the underlying connection.

Returns bytes:

Instrument byte response, including the termination bytes.

Return type:

`bytes`

 wait_for_srq(*timeout=25*, *delay=0.1*)

Wait for a SRQ while keeping the bit asserted.

Parameters:

-

**timeout** (`float`) – Timeout interval in seconds (default: `25`)

-

**delay** (`float`) – Delay between SRQ checks, in seconds (default: `0.1`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument with write_termination appended.

Subclass implementations must not replace this method.

Parameters:

-

**command** (*str*) – Command string sent to the instrument, excluding termination.

-

****kwargs** – Keyword arguments forwarded to the underlying connection.

Return type:

`None`

 write_binary_values(*command*, *values*, *termination=''*, ***kwargs*)

Send binary data to the instrument, such as a waveform for signal generators.

Parameters:

-

**command** (`str`) – command string sent to the instrument

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – iterable containing the binary values

-

**termination** (`str`) – String appended after the payload to end the message. (default: `''`)

-

****kwargs** – Key-word arguments forwarded to `Adapter._format_binary_values()`

Returns:

`int` – number of bytes written

 write_bytes(*content*, ***kwargs*)

Send raw bytes content to the instrument.

Subclass implementations must not replace this method.

Parameters:

-

**content** (*bytes*) – Bytes content sent to the instrument.

-

****kwargs** – Keyword arguments forwarded to the underlying connection.

Return type:

`None`

### Serial adapter

 *class *pymeasure.adapters.SerialAdapter(*port*, *write_termination=''*, *read_termination=''*, ***kwargs*)

Bases: `Adapter`

Adapter for the Python Serial package that enables serial communication with an instrument.

Parameters:

-

**port** (`Union`[`str`, `SerialBase`]) – Serial port

-

**write_termination** (`str`) – String appended to each message before it is written. (default: `''`)

-

**read_termination** (`str`) – String expected at the end of a read message, then removed from the returned text. (default: `''`)

-

****kwargs** – Any supported key-word argument for serial.Serial

 _format_binary_values(*values*, *datatype='f'*, *is_big_endian=False*, *header_fmt='ieee'*)

Encode values into binary form for internal use by `Adapter.write_binary_values()`.

Parameters:

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – data that will be written to the device.

-

**datatype** (`Literal`[`'s'`, `'b'`, `'B'`, `'h'`, `'H'`, `'i'`, `'I'`, `'l'`, `'L'`, `'q'`, `'Q'`, `'f'`, `'d'`]) – single-element format string; accepted codes include ‘b’ and ‘B’, ‘h’ and ‘H’, ‘i’ and ‘I’, ‘l’ and ‘L’, ‘q’ and ‘Q’, ‘f’ and ‘d’, plus ‘s’. (default: `'f'`)

-

**is_big_endian** (`bool`) – boolean that selects endianness. (default: `False`)

-

**header_fmt** (`str`) – header prefix style applied before the data (“ieee”, “hp”, “empty”). (default: `'ieee'`)

Returns:

`bytes` – binary string.

 close()

Close the connection.

Return type:

`None`

 connection*: `Serial`*

 flush_read_buffer()

Clear and drop all data currently in the input buffer.

Return type:

`None`

 read(***kwargs*)

Read until read_termination without including it, or consume the full read buffer.

Subclass implementations must not replace this method.

Parameters:

****kwargs** – Keyword arguments forwarded to the underlying connection.

Returns str:

Instrument reply decoded as ASCII, with read_termination omitted.

Return type:

`str`

 read_binary_values(*header_bytes=0*, *termination_bytes=None*, *dtype=<class 'numpy.float32'>*, *sep=''*, ***kwargs*)

Produces a numpy array from the response to a binary-data query.

Parameters:

-

**header_bytes** (*int*) – Byte count at the message header to skip.

-

**termination_bytes** (*int*) – Byte count to remove from the message tail, or None.

-

**dtype** – NumPy dtype used when formatting the resulting values. (default: `<class 'numpy.float32'>`)

-

**sep** (*string*) – Character separator; when provided, fromstring is used, otherwise frombytes is used.

-

****kwargs** – Additional parameters supplied to the NumPy fromstring / frombytes method.

Returns:

NumPy array of values

Raises:

**ValueError** – raised when the data buffer is empty or malformed

 read_bytes(*count=-1*, *break_on_termchar=False*, ***kwargs*)

Read the requested byte count from the instrument.

Subclass implementations must not replace this method.

Parameters:

-

**count** (*int*) – Bytes requested for the read; -1 means use the complete read buffer.

-

**break_on_termchar** (*bool*) – Stop the read when a termination character is encountered.

-

****kwargs** – Keyword arguments forwarded to the underlying connection.

Returns bytes:

Instrument byte response, including the termination bytes.

Return type:

`bytes`

 write(*command*, ***kwargs*)

Send a string command to the instrument with write_termination appended.

Subclass implementations must not replace this method.

Parameters:

-

**command** (*str*) – Command string sent to the instrument, excluding termination.

-

****kwargs** – Keyword arguments forwarded to the underlying connection.

Return type:

`None`

 write_binary_values(*command*, *values*, *termination=''*, ***kwargs*)

Send binary data to the instrument, such as a waveform for signal generators.

Parameters:

-

**command** (`str`) – command string sent to the instrument

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – iterable containing the binary values

-

**termination** (`str`) – String appended after the payload to end the message. (default: `''`)

-

****kwargs** – Key-word arguments forwarded to `Adapter._format_binary_values()`

Returns:

`int` – number of bytes written

 write_bytes(*content*, ***kwargs*)

Send raw bytes content to the instrument.

Subclass implementations must not replace this method.

Parameters:

-

**content** (*bytes*) – Bytes content sent to the instrument.

-

****kwargs** – Keyword arguments forwarded to the underlying connection.

Return type:

`None`

### Prologix adapter

 *class *pymeasure.adapters.PrologixAdapter(*resource_name*, *address=None*, *auto=False*, *eoi=True*, *eos='\n'*, *gpib_read_timeout=None*, ***kwargs*)

Bases: `VISAAdapter`

Wraps the extra commands required for a Prologix GPIB-USB Adapter while communicating through `VISAAdapter`.

A PrologixAdapter is built from the Prologix-device connection plus the instrument's GPIB address. To share the connection, call `gpib()` to create additional PrologixAdapters for other GPIB addresses.

Parameters:

-

**resource_name** – Connection target for the Prologix hardware, given as a [VISA resource string](https://pyvisa.readthedocs.io/en/latest/introduction/names.html); example: “ASRL5” for COM port 5.

-

**address** – Integer GPIB address for the target instrument. (default: `None`)

-

**auto** – Turn read-after-write on or off and address the instrument to listen. (default: `False`)

-

**eoi** – Turn EOI assertion on or off. (default: `True`)

-

**eos** – Command termination string to set (CR+LF, CR, LF, or “”) (default: `'\\n'`)

-

**gpib_read_timeout** – GPIB read timeout in milliseconds, from 1..3000 (default: `None`)

-

**kwargs** – Extra key-word arguments used when constructing a new serial object

Variables:

**address** – Integer GPIB address for the target instrument.

Usage example:

```python
adapter = PrologixAdapter("ASRL5::INSTR", 7)
sourcemeter = Keithley2400(adapter)  # at GPIB address 7
# generate another instance with a different GPIB address:
adapter2 = adapter.gpib(9)
multimeter = Keithley2000(adapter2)  # at GPIB address 9

```

For Linux user access to the Prologix adapter, create `/etc/udev/rules.d/51-prologix.rules` containing:

```bash
SUBSYSTEMS=="usb",ATTRS{idVendor}=="0403",ATTRS{idProduct}=="6001",MODE="0666"

```

Reload the udev rules afterwards with:

```bash
sudo udevadm control --reload-rules
sudo udevadm trigger

```

Because the Prologix adapter uses one USB CDC channel for both adapter commands and GPIB traffic, keep these constraints in mind:

-

For GPIB reads, call the normal `read()` method.

-

Reads that target the Prologix device's own responses should pass `prologix=True` to `read()` so no GPIB read is requested. The same parameter is needed in “listen-only” mode, where GPIB traffic is forwarded automatically.

-

Send binary bus data with `write_binary_values()` so bytes that the Prologix adapter might parse as commands are escaped correctly. The default behavior of `write_binary_values()` assumes floating-point binary data and prepends IEEE headers; for plain bytes, adjust `datatype` and `header_fmt`:

```python
multimeter.write_binary_values('W', [addr], datatype='B', header_fmt='empty')

```

 _format_binary_values(*values*, *datatype='f'*, *is_big_endian=False*, *header_fmt='ieee'*)

Encode values as binary data for internal use by `write_binary_values()`.

Parameters:

-

**values** – data that will be written to the device.

-

**datatype** – single-element format string; see struct module. (default: `'f'`)

-

**is_big_endian** – boolean that selects endianess. (default: `False`)

-

**header_fmt** – Header prefix style applied before the data (“ieee”, “hp”, “empty”). (default: `'ieee'`)

Returns:

binary string.

Return type:

bytes

 *property *auto

Choose whether instruments are addressed to talk after a command is sent (bool).

Set the Prologix GPIB controller to address instruments to talk automatically after commands so responses can be read. The Read-After-Write feature removes the need for repeated read commands; this property turns it on with True or off with False.

 close()

Close the connection. :rtype: `None`

Note

Close the resource connection for every adapter currently sharing it, such as adapters on one GPIB line.

 connection*: ProtocolAdapter | pyvisa.resources.MessageBasedResource*

 *property *eoi

Choose whether the final character of a command sent over GPIB port asserts EOI (bool).

Some instruments only recognize command completion when EOI signal is asserted.

 *property *eos

Control GPIB termination characters (str).

possible values:

-

CR+LF

-

CR

-

LF

-

empty string

On host input, unescaped LF, CR, and ESC characters are stripped, then the GPIB terminators specified by this command are appended before data is sent to instruments. This command does not change data received from instruments over GPIB port.

 flush_read_buffer()

Clear and drop the input buffer.

Following pyvisa behavior, the read and receive buffers are discarded. If the read buffer contained data without an END-indicator, the device is read until an END indicator appears, which drops that data.

Return type:

`None`

 gpib(*address*, ***kwargs*)

Return a PrologixAdapter object for the requested GPIB address while reusing the Serial connection shared by other invocations of this function.

Parameters:

-

**address** – Integer GPIB address for the target instrument

-

**kwargs** – Arguments for the initialization

Returns:

PrologixAdapter for specific GPIB address

 *property *gpib_read_timeout

Set or read the GPIB communication timeout value in milliseconds.

possible values: 1 - 3000

 read(***kwargs*)

Read until read_termination without including it, or consume the full read buffer.

Subclass implementations must not replace this method.

Parameters:

****kwargs** – Keyword arguments forwarded to the underlying connection.

Returns str:

Instrument reply decoded as ASCII, with read_termination omitted.

Return type:

`str`

 read_binary_values(*header_bytes=0*, *termination_bytes=None*, *dtype=<class 'numpy.float32'>*, *sep=''*, ***kwargs*)

Produces a numpy array from the response to a binary-data query.

Parameters:

-

**header_bytes** (*int*) – Byte count at the message header to skip.

-

**termination_bytes** (*int*) – Byte count to remove from the message tail, or None.

-

**dtype** – NumPy dtype used when formatting the resulting values. (default: `<class 'numpy.float32'>`)

-

**sep** (*string*) – Character separator; when provided, fromstring is used, otherwise frombytes is used.

-

****kwargs** – Additional parameters supplied to the NumPy fromstring / frombytes method.

Returns:

NumPy array of values

Raises:

**ValueError** – raised when the data buffer is empty or malformed

 read_bytes(*count=-1*, *break_on_termchar=False*, ***kwargs*)

Read the requested byte count from the instrument.

Subclass implementations must not replace this method.

Parameters:

-

**count** (*int*) – Bytes requested for the read; -1 means use the complete read buffer.

-

**break_on_termchar** (*bool*) – Stop the read when a termination character is encountered.

-

****kwargs** – Keyword arguments forwarded to the underlying connection.

Returns bytes:

Instrument byte response, including the termination bytes.

Return type:

`bytes`

 reset()

Issue a power-on reset to the controller.

This operation lasts about 5 seconds; input received during that interval is ignored, and the connection is closed.

 *property *version

Return the Prologix controller version string.

 wait_for_srq(*timeout=25*, *delay=0.1*)

Waits for a SRQ and keeps the bit asserted.

Parameters:

-

**timeout** – Timeout interval in seconds. (default: `25`)

-

**delay** – Delay between SRQ checks, in seconds. (default: `0.1`)

Raises:

**TimeoutError** – raises “Waiting for SRQ timed out.”

 write(*command*, ***kwargs*)

Send a string command to the instrument with write_termination appended.

If `address` has a GPIB address, that address is sent before the command.

Parameters:

-

**command** (*str*) – Command string sent to the instrument, excluding termination.

-

**kwargs** – Keyword arguments forwarded to the underlying connection.

 write_binary_values(*command*, *values*, ***kwargs*)

Send binary data to the instrument, such as a waveform for signal generators.

values are encoded as an IEEE 488.2 Definite Length Arbitrary Block Response Data block.

Parameters:

-

**command** – SCPI command sent to the instrument

-

**values** – iterable containing the binary values

-

**kwargs** – Key-word arguments forwarded to `_format_binary_values()`

Returns:

number of bytes written

 write_bytes(*content*, ***kwargs*)

Send raw bytes content to the instrument.

Subclass implementations must not replace this method.

Parameters:

-

**content** (*bytes*) – Bytes content sent to the instrument.

-

****kwargs** – Keyword arguments forwarded to the underlying connection.

Return type:

`None`

### Test adapters

Utilities used for writing tests.

 pymeasure.test.expected_protocol(*instrument_cls*, *comm_pairs*, *connection_attributes=None*, *connection_methods=None*, ***kwargs*)

Context manager for checking instrument commands sent and received when no device is attached.

Provide the instrument class plus expected command-response pairs; the context manager then checks that code inside the block sends the intended messages.

Protocol definitions omit terminators because those usually belong to the communication method, i.e. Adapter, rather than to the protocol.

Parameters:

-

**instrument_cls** (*pymeasure.Instrument*) – [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument) subclass that will be instantiated.

-

**comm_pairs** (*list**[**2-tuples**[**str**]**]*) – Command-response pair list, i.e. 2-tuples such as (‘VOLT?’, ‘3.14’). ‘None’ marks a missing pair member (command or response), for example (None, ‘RESP1’). Termination characters are not included in commands or responses.

-

**connection_attributes** (`Optional`[`dict`[`str`, `Any`]]) – Dictionary mapping connection attributes to their values. (default: `None`)

-

**connection_methods** (`Optional`[`dict`[`str`, `Any`]]) – Dictionary mapping connection method names to their return values. (default: `None`)

-

****kwargs** – Keyword arguments used when instantiating the instrument.

Return type:

`Generator`[`TypeVar`(`Inst`, bound= [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)), `Any`, `None`]
