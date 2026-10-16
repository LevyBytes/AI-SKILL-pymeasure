# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X

*class *pymeasure.instruments.advantest.advantestR624X.AdvantestR624X(*adapter*, *name='R624X Source meter Base Class'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

High-level interface for the Advantest R624X series SourceMeter, covering channel A and B instrument control.

Base class shared by AdvantestR6245 and AdvantestR6246 devices. Create AdvantestR6245 or AdvantestR6246 instances directly instead of instantiating this class, as in the example below:

```python
from pymeasure.instruments.advantest.advantestR624X import AdvantestR6246, CurrentRange

smu = AdvantestR6246("GPIB::1")
smu.reset()                                                     # Set default parameters
smu.ch_A.current_source(source_range = CurrentRange.FIXED_60mA,
                        source_value = 0,                       # Source current at 0 A
                        voltage_compliance = 10)                # Voltage compliance at 10 V
smu.ch_A.enable_source()                                        # Enables the source output
smu.ch_A.measure_voltage()
smu.ch_A.current_change_source = 5e-3                           # Change to 5mA
print(smu.read_measurement())                                   # Read and print the voltage
smu.ch_A.standby()                                              # Put channel A in standby

```
