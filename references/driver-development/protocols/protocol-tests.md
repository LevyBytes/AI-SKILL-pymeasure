# Protocol tests

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

- Simple instrument test: `tests/instruments/keithley/test_keithley2000.py`

- Multi-channel instrument test: `tests/instruments/tektronix/test_afg3152.py`

- Frame-based communication test: `tests/instruments/hcp/tc038.py`
