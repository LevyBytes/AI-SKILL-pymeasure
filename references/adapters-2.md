# Adapters (part 2)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

*class *pymeasure.adapters.ProtocolAdapter(*comm_pairs=None*, *connection_attributes=None*, *connection_methods=None*, ***kwargs*)

Bases: `Adapter`

Testing adapter for the command exchange protocol without requiring instrument hardware.

Use this adapter mainly with `pymeasure.test.expected_protocol()`.

The `connection` attribute uses a `unittest.mock.MagicMock`, so each invoked member returns normally. To define a result, assign `adapter.connection.some_method.return_value = 7`; then `adapter.connection.some_method()` returns 7. You can also confirm the connection method ran with `assert adapter.connection.some_method.called is True`. Dictionaries may supply return values for attributes and methods.

Parameters:

-

**comm_pairs** (*list*) - List of reference message-pair tuples. In each tuple, the first entry is sent to the instrument and the second entry is the reply. `None` marks a missing pair member, either write or read. Termination characters are **not** part of the messages.

-

**connection_attributes** (`Optional`[`dict`]) - Dictionary containing connection attributes with their values. (default: `None`)

-

**connection_methods** (`Optional`[`dict`]) - Dictionary mapping connection method names to the values they return. (default: `None`)

 connection*: `MagicMock`*

 flush_read_buffer()

Clear the input buffer by flushing and discarding it.

Following pyvisa behavior, the read buffer contents are discarded; when the read buffer held data without an END-indicator, the device is read until an END indicator is encountered, losing data in the process.

Return type:

`None`

 *class *pymeasure.adapters.FakeAdapter(*log=None*, ***kwargs*)

Bases: `Adapter`

Supplies a fake debugging adapter that echoes the command, making arbitrary values testing possible.

```python
a = FakeAdapter()
assert a.read() == ""
a.write("5")
assert a.read() == "5"
assert a.read() == ""
assert a.ask("10") == "10"
assert a.values("10") == [10]

```

 close()

Close the connection.

Return type:

`None`

 connection*: `ConnectionProtocol`*

 flush_read_buffer()

Flush and discard the input buffer; subclasses must implement this.

Return type:

`None`

 read(***kwargs*)

Read either the whole read buffer or data up to, but not including, read_termination.

A subclass must not override this.

Parameters:

****kwargs** - Keyword arguments passed to the connection itself.

Returns str:

Instrument ASCII response, with read_termination excluded.

Return type:

`str`

 read_binary_values(*header_bytes=0*, *termination_bytes=None*, *dtype=<class 'numpy.float32'>*, *sep=''*, ***kwargs*)

Return a numpy array produced by querying binary data.

Parameters:

-

**header_bytes** (*int*) - Count of header bytes to ignore.

-

**termination_bytes** (*int*) - Count of bytes to remove from the message end, or None.

-

**dtype** - NumPy data type used to format the values. (default: `<class 'numpy.float32'>`)

-

**sep** (*string*) - Character separator. If provided, use fromstring; otherwise use frombytes.

-

****kwargs** - Additional arguments for the NumPy fromstring / frombytes method.

Returns:

NumPy array of values

Raises:

**ValueError** - when the data buffer is empty or malformed

 read_bytes(*count=-1*, *break_on_termchar=False*, ***kwargs*)

Read a specified byte count from the instrument.

A subclass must not override this.

Parameters:

-

**count** (*int*) - Byte count to read. A value of -1 means the whole read buffer is read.

-

**break_on_termchar** (*bool*) - Stop reading when a termination character is reached.

-

****kwargs** - Keyword arguments passed to the connection itself.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 write(*command*, ***kwargs*)

Send a string command to the instrument after appending write_termination.

A subclass must not override this.

Parameters:

-

**command** (*str*) - Command string sent to the instrument, without termination.

-

****kwargs** - Keyword arguments passed to the connection itself.

Return type:

`None`

 write_binary_values(*command*, *values*, *termination=''*, ***kwargs*)

Send binary data to the instrument, for example a signal-generator waveform.

Parameters:

-

**command** (`str`) - command string sent to the instrument

-

**values** (`Sequence`[`Union`[`int`, `float`]]) - iterable representing binary values

-

**termination** (`str`) - String appended after the data to terminate the message. (default: `''`)

-

****kwargs** - Key-word arguments forwarded to `Adapter._format_binary_values()`

Returns:

`int` – number of bytes written

 write_bytes(*content*, ***kwargs*)

Send byte content to the instrument.

A subclass must not override this.

Parameters:

-

**content** (*bytes*) - Bytes written to the instrument.

-

****kwargs** - Keyword arguments passed to the connection itself.

Return type:

`None`

 *class *pymeasure.generator.Generator

Creates tests from recorded communication with an instrument.

Example usage:

```python
g = Generator()
inst = g.instantiate(TC038, "COM5", 'hcp', adapter_kwargs={'baud_rate': 9600})
inst.information  # returns the 'information' property and adds it to the tests
inst.setpoint = 20
inst.setpoint == 20  # should be True
g.write_file("test_tc038.py")  # write the tests to a file

```

 instantiate(*instrument_class*, *adapter*, *manufacturer*, *adapter_kwargs=None*, ***kwargs*)

Create the instrument and record the communication used during instantiation.

..note:

```python
You have to give all keyword arguments necessary for adapter instantiation in
`adapter_kwargs`, even those, which are defined somewhere in the instrument's
``__init__`` method, be it as a default value, be it directly in the
``Instrument.__init__()`` call.

```

Parameters:

-

**instrument_class** - Instrument class to test.

-

**adapter** - Adapter, either an instance or str, used for instrument instantiation.

-

**manufacturer** - Module from which the instrument is imported, e.g. 'hcp' when instrument_class is 'pymeasure.hcp.tc038'.

-

**adapter_kwargs** - Keyword arguments used for adapter instantiation (see note above). (default: `None`)

-

****kwargs** - Keyword arguments for the instrument instantiation.

Returns:

A man-in-the-middle instrument usable like a normal instrument.

 parse_stream()

Parse the unread portion of the stream.

 test_method(*method_name*, **args*, ***kwargs*)

Test a call to method_name on the instruments with args and kwargs.

 test_property_getter(*property*)

Test reading the instrument property and append it to the list.

 test_property_setter(*property*, *value*)

Test assigning value to the instrument property and append it to the list.

 test_property_setter_batch(*property*, *values*)

Test assigning property to every element in values.

 write_file(*filename='tests.py'*)

Write the tests to the file.

Parameters:

**filename** - File name for saving the tests; it may include a path, e.g. `/tests/test_abc.py`. (default: `'tests.py'`)

 write_getter_test(*file*, *property*, *parameters*)

Write a getter test.

 write_init_test(*file*)

Write the header plus the init test.

 write_method_test(*file*, *method*, *parameters*)

Write one method test.

 write_method_tests(*file*)

Write every parametrized method test in alphabetic order.

 write_property_tests(*file*)

Write property tests in alphabetic order.

When both getter and setter exist, place the setter test first.

 write_setter_test(*file*, *property*, *parameters*)

Write a setter test.
