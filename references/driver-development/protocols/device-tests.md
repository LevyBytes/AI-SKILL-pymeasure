# Device tests

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
