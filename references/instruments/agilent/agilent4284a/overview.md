# pymeasure.instruments.agilent.Agilent4284A

*class *pymeasure.instruments.agilent.Agilent4284A(*adapter*, *name='Agilent 4284A LCR meter'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Agilent 4284A precision LCR meter.

```python
from pymeasure.instruments.agilent import Agilent4284A

agilent = Agilent4284A("GPIB::1::INSTR")

agilent.reset()                         # Return instrument settings to default
                                          # values
agilent.frequency = 10e3                # Set frequency to 10 kHz
agilent.voltage = 0.02                  # Set AC voltage to 20 mV
agilent.mode = 'ZTR'                    # Set impedance mode to measure
                                          # impedance magnitude [Ohm] and phase
                                          # [rad]
agilent.sweep_measurement(
    'frequency', [1e4, 1e3, 100]        # Perform frequency sweep measurement
)                                       # at 10 kHz, 1 kHz, and 100 Hz
agilent.enable_high_power()             # Enable upper current, voltage, and
                                          # bias limits, if properly configured.

agilent.correction.open_enabled = True     # Enable the OPEN correction
agilent.correction.spot1.enabled = True    # Enable the correction for SPOT1
agilent.correction.spot1.frequency = 10e3  # Set SPOT1 frequency to 10 kHz
agilent.correction.spot1.measure_open()    # Measure the OPEN structure for SPOT1

```
