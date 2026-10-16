# pymeasure.instruments.temptronic.ATS545

*class *pymeasure.instruments.temptronic.ATS545(*adapter*, *name='Temptronic ATS-545 Thermostream'*, ***kwargs*)

Bases: [`ATSBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/temptronic/temptronic_base.html#pymeasure.instruments.temptronic.ATSBase)

Represents the TemptronicATS545 instrument.

Coding example

```python
from pymeasure.instruments.temptronic.temptronic_ats545 import ATS545

ts = ATS545('ASRL3::INSTR')  # replace adapter address
ts.configure()  # basic configuration (defaults to T-DUT)
ts.start()  # starts flow (head position not changed)
ts.set_temperature(25)  # sets temperature to 25 degC
ts.wait_for_settling()  # blocks script execution and polls for settling
ts.shutdown(head=False)  # disables thermostream, keeps head down

```
