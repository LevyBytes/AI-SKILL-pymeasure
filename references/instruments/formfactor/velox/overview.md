# pymeasure.instruments.formfactor.Velox

*class *pymeasure.instruments.formfactor.Velox(*adapter*, *name='FormFactor Velox'*, *timeout=40000*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for the FormFactor Velox wafer prober.

Example showing a full-wafer measurement:

```python
from pymeasure.instruments.formfactor.velox import Velox

prober = Velox("GPIB0::28::INSTR")  # replace the resource to your needs
coordinates = prober.wafermap.step_first_die()  # move to the first die in the wafermap
while not self.wafermap.end_reached:
    prober.chuck.move_contact()  # move to contact height
    # ...
    # code for measurement, processing and storing data
    # ...
    prober.chuck.move_separation()  # move to separation height
    coordinates = prober.wafermap.step_next_die()  # move to the next die in the wafermap

```
