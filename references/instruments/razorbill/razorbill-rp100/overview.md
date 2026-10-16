# pymeasure.instruments.razorbill.razorbillRP100

*class *pymeasure.instruments.razorbill.razorbillRP100(*adapter*, *name='Razorbill RP100 Piezo Stack Powersupply'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Represents Razorbill RP100 strain cell controller

```python
from pymeasure.instruments.razorbill.razorbillRP100 import razorbillRP100

scontrol = razorbillRP100("ASRL/dev/ttyACM0::INSTR")

scontrol.output_1 = True      # turns output on
scontrol.slew_rate_1 = 1      # sets slew rate to 1V/s
scontrol.voltage_1 = 10       # sets voltage on output 1 to 10V

```
