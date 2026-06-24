# Advanced Communication, Tests

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Advanced communication protocols; Writing tests; Adding instruments.

## Advanced communication protocols

### Advanced communication protocols

Devices that use addresses, checksums, or similar framing may need logic beyond the default protocol. Usually, overriding [`Instrument.write`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument.write) and [`Instrument.read`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument.read) is enough.

### Instrument’s inner workings

For complicated protocols, first separate the responsibilities inside an instrument driver.

The [`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter) layer offers [`write()`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter.write) and [`read()`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter.read) for string traffic, plus [`write_bytes()`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter.write_bytes) and [`read_bytes()`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter.read_bytes) for byte-oriented messages. Those low-level entry points record the traffic that passes through them before delegating to adapter-specific private methods such as `VISAAdapter._read`. Binary payloads, for example waveforms, use [`write_binary_values()`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter.write_binary_values) and [`read_binary_values()`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter.read_binary_values), which build on the same communication path. Driver code normally calls the identically named methods on [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument), letting the instrument class route the call to the adapter and keeping the implementation compact.

At the [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument) level, [`write()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument.write) and [`read()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument.read) are the central primitives for communication. The pymeasure property helpers, including [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control), [`Instrument.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement), and [`Instrument.setting`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.setting), ultimately depend on them, and most driver methods/properties tend to do the same. For a given instrument, `write()` should send a general string command in the form the device accepts. Likewise, `read()` should provide a general string response that later parsing code can handle.

The getter provided by [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) reaches those primitives indirectly. It runs `values()`, which calls `ask()` and turns the returned string into values the driver can use. `ask()` issues the readout command through `write()`, optionally pauses with `wait_for()`, and obtains the reply with `read()`.

By comparison, `Instrument.binary_values` writes its command with `write()`, delays through `wait_till_read()`, and then obtains data with [`Adapter.read_binary_values`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter.read_binary_values).

### Adding a device address and adding delay

Consider a device whose protocol puts its address in the first three characters and echoes responses in that format. The customization is small: `write()` adds the address before the command, while `read()` removes it and performs validation. The same pattern could attach a checksum. Because the device also needs a pause after receiving a command before it answers, `wait_for()` should always apply a fixed delay.

```python
class ExtremeCommunication(Instrument):
    """Control the ExtremeCommunication instrument.

    :param address: The device address for the communication.
    :param query_delay: Wait time after writing and before reading in seconds.
    """
    def __init__(self, adapter, name="ExtremeCommunication", address=0, query_delay=0.1):
        super().__init__(adapter, name)
        self.address = f"{address:03}"
        self.query_delay = query_delay

    def write(self, command):
        """Add the device address in front of every command before sending it."""
        super().write(self.address + command)

    def wait_for(self, query_delay=0):
        """Wait for some time.

        :param query_delay: override the global query_delay.
        """
        super().wait_for(query_delay or self.query_delay)

    def read(self):
        """Read from the device and check the response.

        Assert that the response starts with the device address.
        """
        got = super().read()
        if got.startswith(self.address):
            return got[3:]
        else:
            raise ConnectionError(f"Expected message address '{self.address}', but read '{got[3:]}' for wrong address '{got[:3]}'.")

    voltage = Instrument.measurement(
        ":VOLT:?", """Measure the voltage in Volts.""")

```

With `address=12` at initialization time, requesting voltage sends `"012:VOLT:?"` and the driver should look for a reply that starts with `"012"`.

### Bytes communication

Certain instruments exchange raw bytes instead of ASCII strings. In that situation, implement `write()` and `read()` by invoking `write_bytes()` and `read_bytes()`. The next example models a register-based instrument where reads and writes are performed with byte messages.

```python
class ExtremeBytes(Instrument):
    """Control the ExtremeBytes instrument with byte-based communication."""
    def __init__(self, adapter, name="ExtremeBytes"):
        super().__init__(adapter, name)

    def write(self, command):
        """Write to the device according to the comma separated command.

        :param command: R or W for read or write, hexadecimal address, and data.
        """
        function, address, data = command.split(",")
        b = [0x03] if function == "R" else [0x10]
        b.extend(int(address, 16).to_bytes(2, byteorder="big"))
        b.extend(int(data).to_bytes(length=8, byteorder="big", signed=True))
        self.write_bytes(bytes(b))

    def read(self):
        """Read the response and return the data as a string, if applicable."""
        response = self.read_bytes(2)  # return type and payload
        if response[0] == 0x00:
            raise ConnectionError(f"Device error of type {response[1]} occurred.")
        if response[0] == 0x03:
            # read that many bytes and return them as an integer
            data = self.read_bytes(response[1])
            return str(int.from_bytes(data, byteorder="big", signed=True))
        if response[0] == 0x10 and response[1] != 0x00:
            raise ConnectionError(f"Writing to the device failed with error {response[1]}")

    voltage = Instrument.control(
        "R,0x106,1", "W,0x106,%i",
        """Control the output voltage in mV.""",
    )

```

## Writing tests

### Writing tests

Good tests make driver code easier to trust. The pymeasure project already includes tests for its own implementation, stored under the `tests` directory. CI runs them automatically, and you can execute the same suite locally with `pytest`.

For a new instrument, focus first on tests for the *instrument driver* you are adding. Instrument tests fall into two categories. One category runs without hardware and checks that the driver sends and receives the expected protocol messages, such as those described in a device manual; these are "protocol tests". The other category runs against a connected device.

Add device test modules under `tests/instruments/...`, matching the package layout used by the corresponding instrument implementations. Existing instrument tests in that tree are useful patterns to follow.

### Protocol tests

To check that driver code behaves as intended, cover each part of the implementation. The [`expected_protocol()`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.test.expected_protocol) context manager, backed by a [`ProtocolAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.ProtocolAdapter), stands in for a device and verifies that communications caused by the `with` block match the expected send/receive sequence.

```python
import pytest

from pymeasure.test import expected_protocol

from pymeasure.instruments.extreme5000 import Extreme5000

def test_voltage():
    """Verify the communication of the voltage getter."""
    with expected_protocol(
        Extreme5000,
        [(":VOLT 0.345", None),
         (":VOLT?", "0.3000")],
    ) as inst:
        inst.voltage = 0.345
        assert inst.voltage == 0.3

```

The example imports pytest, expected_protocol, and the instrument class that the test will exercise.

The first argument, Extreme5000, identifies the class being exercised.

Assigning the voltage makes the driver send `":VOLT 0.345"` and receive no reply (`None`). Reading the voltage sends `":VOLT?"` and should receive `"0.3000"`. The expected protocol therefore contains two send/receive pairs, supplied as the second argument.

The context manager yields `inst`, an instance of the target class. Use that object, for example by accessing its properties, to trigger the operations represented by the protocol.

An Exception is raised when the driver's communication differs from the expected messages.

Note

List expected messages **without** termination characters, because termination depends on the connection and is added by the regular adapter, for example `VISAAdapter`.

The test suite includes protocol-test examples for comparison:

-

Simple instrument test: `tests/instruments/keithley/test_keithley2000.py`

-

Multi-channel instrument test: `tests/instruments/tektronix/test_afg3152.py`

-

Frame-based communication test: `tests/instruments/hcp/tc038.py`

### Test generator

If working code and access to the hardware already exist, the [`Generator`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.generator.Generator) can help create tests. Put a TestGenerator between your code and the instrument; it records method calls, device traffic, and any return values, then emits tests from the log.

```python
from pymeasure.generator import Generator
from pymeasure.instruments.hcp import TC038

generator = Generator()
inst = generator.instantiate(TC038, adapter, 'hcp', adapter_kwargs={'baud_rate': 9600})

```

This first code block imports Generator and creates a middle-man instrument. Calling `instantiate()` constructs the instrument and captures startup communication. Generator supplies a special adapter for talking to the device, but it cannot introspect the instrument's `__init__()`. For that reason, every connection option must be passed through the `adapter_kwargs` dictionary, including options normally set in `__init__()`. Those adapter arguments are omitted from the generated tests. Instrument-level arguments, such as a RS485 address, can be passed as keyword arguments, and those extra keyword arguments are written into the tests.

After that, use `inst` exactly like a normally constructed instrument, for example `inst = TC038(adapter)`, where `adapter` is a resource string. Once you have read or written properties and called methods, ask the Generator to write the resulting tests to a file.

```python
inst.information  # returns the 'information' property, e.g. 'UT150333 V01.R001111222233334444'
inst.setpoint = 20
assert inst.setpoint == 20
inst.setpoint = 60

generator.write_file(file)

```

The generated contents for `file` are:

```none
import pytest

from pymeasure.test import expected_protocol
from pymeasure.instruments.hcp import TC038

def test_init():
    with expected_protocol(
            TC038,
            [(b'\x0201010WRS01D0002\x03', b'\x020101OK\x03')],
    ):
        pass  # Verify the expected communication.

def test_information_getter():
    with expected_protocol(
            TC038,
            [(b'\x0201010WRS01D0002\x03', b'\x020101OK\x03'),
             (b'\x0201010INF6\x03', b'\x020101OKUT150333 V01.R001111222233334444\x03')],
    ) as inst:
        assert inst.information == 'UT150333 V01.R001111222233334444'

@pytest.mark.parametrize("comm_pairs, value", (
    ([(b'\x0201010WRS01D0002\x03', b'\x020101OK\x03'),
      (b'\x0201010WWRD0120,01,00C8\x03', b'\x020101OK\x03')],
     20),
    ([(b'\x0201010WRS01D0002\x03', b'\x020101OK\x03'),
      (b'\x0201010WWRD0120,01,0258\x03', b'\x020101OK\x03')],
     60),
))
def test_setpoint_setter(comm_pairs, value):
    with expected_protocol(
            TC038,
            comm_pairs,
    ) as inst:
        inst.setpoint = value

def test_setpoint_getter():
    with expected_protocol(
            TC038,
            [(b'\x0201010WRS01D0002\x03', b'\x020101OK\x03'),
             (b'\x0201010WRDD0120,01\x03', b'\x020101OK00C8\x03')],
    ) as inst:
        assert inst.setpoint == 20.0

```

### Device tests

Testing against real hardware can also be worthwhile. Put any required setup steps, such as connecting a probe to the test output, in the test file or method header, and include the connection configuration such as the serial port. To separate these from protocol tests, name the module `test_instrumentName_with_device.py` when the device is named `instrumentName`.

For easier reuse with someone else's hardware, define a `pytest.fixture` that creates the instrument instance. Use the argument name `connected_device_address` and give the fixture a scope that opens only one device connection. This provides two behaviors: the device address can be supplied with the `--device-address` command line argument, and pytest skips tests that need connected hardware unless that address is supplied. Any test requiring a device connection should receive `connected_device_address` or a fixture derived from it.

A minimal fixture returning a connected instrument instance can be written like this:

```python
@pytest.fixture(scope="module")
def extreme5000(connected_device_address):
    instr = Extreme5000(connected_device_address)
    # ensure the device is in a defined state, e.g. by resetting it.
    return instr

```

Because this fixture accepts `connected_device_address`, automatic test runs skip it. A test function can then request the fixture as shown here:

```python
def test_voltage(extreme5000):
    extreme5000.voltage = 0.345
    assert extreme5000.voltage == 0.3

```

Specifying the fixture name, here `extreme5000`, means a plain `pytest` invocation skips these tests by default.

You may also create derived fixtures, for instance one that prepares the device in a chosen state:

```python
@pytest.fixture
def auto_scaled_extreme5000(extreme5000):
    extreme5000.auto_scale()
    return extreme5000

```

Here, omit the fixture scope so pytest calls the fixture separately for each test function that uses it.

Run a device test by passing the target address with `--device-address` and narrowing pytest to the relevant tests. Use `-k` as a filter or pass the test filename directly. For tests stored in `test_extreme5000_with_device.py`, one example command is `pytest -k extreme5000 --device-address "TCPIP::192.168.0.123::INSTR"`.

Tests that need human action should be skipped explicitly. Add `@pytest.mark.skip(reason="A human needs to press a button.")` before the test function.

## Adding instruments

### Adding instruments

Adding an instrument under `pymeasure.instruments` is a valuable way to improve PyMeasure. Even a driver with only a small feature set can unblock later work, because other users may need the same model.

Before you start, read the PyMeasure [contributing work-flow](https://pymeasure.readthedocs.io/en/latest/dev/contribute.html), which explains how to add a development-version feature such as a new instrument.

Pymeasure instruments talk to devices by sending bytes, either raw or as ASCII characters encoded into bytes. [property creators](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#properties) make python properties easier to define; [channels](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html#channels) provide a similar helper path for channel implementations. Use [tests](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/tests.html#tests) to keep the implementation maintainable and smoother to evolve.

The sections below outline the expected layout for instrument code.

- [File structure](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html)
  - [Changing the init file](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#updating-the-init-file)
  - [Add test files](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#add-test-files)
  - [Adding documentation](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#adding-documentation)

- [Instrument file](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#instrument-file)
- [User-facing interface for your instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#your-instrument-s-user-interface)
  - [Common instrument types](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#common-instrument-types)
  - [Handling status codes and indicator values](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#managing-status-codes-or-other-indicator-values)

- [Defining default connection settings](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#defining-default-connection-settings)
  - [Single interface](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#single-interface)
  - [Multiple interfaces](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/instrument.html#multiple-interfaces)

- [Writing properties](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html)
  - [Property factory helpers](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#the-property-factories)
  - [Validator-based value restrictions](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#restricting-values-with-validators)
  - [Mapping values](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#mapping-values)
  - [Boolean properties](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#boolean-properties)
  - [Processing values before setting them](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#processing-of-set-values)
  - [Processing values returned by the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#processing-of-return-values)
  - [Checking the instrument error state](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#checking-the-instrument-for-errors)
  - [Working with multiple values](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#using-multiple-values)
  - [Dynamic properties](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#dynamic-properties)

- [Sharing behavior across similar instruments](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#instruments-with-similar-features)
  - [Instrument families with differing parameter values](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#instrument-family-with-different-parameter-values)
  - [Sharing command syntax across instruments](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#instruments-with-similar-command-syntax)

- [Channel-based instruments](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html)
  - [Creating a channel with `ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html#adding-a-channel-with-channelcreator)
  - [Creating multiple channels with `MultiChannelCreator`](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html#adding-multiple-channels-with-multichannelcreator)
  - [Advanced channel management](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html#advanced-channel-management)

- [Advanced communication protocols](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/advanced_communication.html)
  - [Instrument’s inner workings](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/advanced_communication.html#instrument-s-inner-workings)
  - [Adding device addressing and delay handling](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/advanced_communication.html#adding-a-device-address-and-adding-delay)
  - [Bytes communication](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/advanced_communication.html#bytes-communication)

- [Writing tests](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/tests.html)
  - [Protocol tests](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/tests.html#protocol-tests)
  - [Device tests](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/tests.html#device-tests)

- [Implementation-challenge solutions](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/solutions.html)
  - [General issues](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/solutions.html#general-issues)
  - [Communication protocol issues](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/solutions.html#communication-protocol-issues)
  - [Channels](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/solutions.html#channels)
