# pymeasure.generator.Generator

*class *pymeasure.generator.Generator

Creates tests from recorded communication with an instrument.

Example usage:

```python
from pymeasure.generator import Generator
from pymeasure.instruments.hcp.tc038 import TC038

g = Generator()
inst = g.instantiate(TC038, "COM5", 'hcp', adapter_kwargs={'baud_rate': 9600})
inst.information  # returns the 'information' property and adds it to the tests
inst.setpoint = 20
inst.setpoint == 20  # should be True
g.write_file("test_tc038.py")  # write the tests to a file

```
