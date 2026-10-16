# pymeasure.instruments.signalrecovery.DSP7225

*class *pymeasure.instruments.signalrecovery.DSP7225(*adapter*, *name='Signal Recovery DSP 7225'*, ***kwargs*)

Bases: `DSPBase`

Models the Signal Recovery DSP 7225 lock-in amplifier.

This class takes its commands from the DSPBase parent class and uses dynamic properties for several properties.

```python
from pymeasure.instruments.signalrecovery.dsp7225 import DSP7225

lockin7225 = DSP7225("GPIB0::12::INSTR")
lockin7225.imode = "voltage mode"       # Set to measure voltages
lockin7225.reference = "internal"       # Use internal oscillator
lockin7225.fet = 1                      # Use FET pre-amp
lockin7225.shield = 0                   # Ground shields
lockin7225.coupling = 0                 # AC input coupling
lockin7225.time_constant = 0.10         # Filter time set to 100 ms
lockin7225.sensitivity = 2E-3           # Sensitivity set to 2 mV
lockin7225.frequency = 100              # Set oscillator frequency to 100 Hz
lockin7225.voltage = 1                  # Set oscillator amplitude to 1 V
lockin7225.gain = 20                    # Set AC gain to 20 dB
print(lockin7225.x)                     # Measure X channel voltage
lockin7225.shutdown()                    # Instrument shutdown

```
