# General Information

Use [armstrap/pyvirtualbench](https://github.com/armstrap/armstrap-pyvirtualbench), the Python binding for the VirtualBench C-API. This Instrument driver talks through that pyvirtualbench Python wrapper only.

### Examples

Documentation is still pending; see the pyvirtualbench repository examples for usage patterns.

Minimal example for toggling DIO module digital lines.

```python
from pymeasure.instruments.ni import VirtualBench

vb = VirtualBench(device_name='VB8012-3057E1C')
line = 'dig/2'  # may be list of lines
# initialize DIO module -> available via vb.dio
vb.acquire_digital_input_output(line, reset=False)

vb.dio.write(self.line, {True})
sleep(1000)
vb.dio.write(self.line, {False})

vb.shutdown()

```
