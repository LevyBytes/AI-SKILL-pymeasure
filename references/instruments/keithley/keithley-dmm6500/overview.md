# pymeasure.instruments.keithley.KeithleyDMM6500

*class *pymeasure.instruments.keithley.KeithleyDMM6500(*adapter*, *name='Keithley DMM6500 6½-Digit Multimeter'*, *read_termination='\n'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model the Keithely DMM6500 6??-Digit Multimeter and expose a higher-level API for instrument operations. Communication in this class is limited to the `SCPI` command set; see `command_set` as well.

```python
from pymeasure.instruments.keithley.keithleyDMM6500 import KeithleyDMM6500

# Access via LAN
ip_address = "xxx.xxx.xxx.xxx"
dmm = KeithleyDMM6500(f"TCPIP::{ip_address}::inst0::INSTR")

```

You may identify the DMM6500 USB port name with PyVISA, then pass that name to `KeithleyDMM6500`.

```python
from pymeasure.instruments.keithley.keithleyDMM6500 import KeithleyDMM6500

import pyvisa
rm = pyvisa.ResourceManager()
resources = rm.list_resources()

# assume there is only one USB instruments
# Ex. ('USB0::1510::25856::01234567::0::INSTR')

dmm = KeithleyDMM6500( resources[0] )

# Measure voltage
dmm.measure_voltage()
print(dmm.voltage)

# Measure AC voltage
dmm.measure_voltage(ac=True)
print(dmm.voltage)

```
