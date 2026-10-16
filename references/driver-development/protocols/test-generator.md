# Test generator

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

```python
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
