# pymeasure.instruments.signalrecovery.DSP7265

*class *pymeasure.instruments.signalrecovery.DSP7265(*adapter*, *name='Signal Recovery DSP 7265'*, ***kwargs*)

Bases: `DSPBase`

Models the Signal Recovery DSP 7265 lock-in amplifier.

This class derives its commands from DSPBase and uses dynamic properties for multiple properties, with extra behavior layered on.

```python
from pymeasure.instruments.signalrecovery.dsp7265 import DSP7265

lockin7265 = DSP7265("GPIB0::12::INSTR")
lockin7265.imode = "voltage mode"       # Set to measure voltages
lockin7265.reference = "internal"       # Use internal oscillator
lockin7265.fet = 1                      # Use FET pre-amp
lockin7265.shield = 0                   # Ground shields
lockin7265.coupling = 0                 # AC input coupling
lockin7265.time_constant = 0.10         # Filter time set to 100 ms
lockin7265.sensitivity = 2E-3           # Sensitivity set to 2 mV
lockin7265.frequency = 100              # Set oscillator frequency to 100 Hz
lockin7265.voltage = 1                  # Set oscillator amplitude to 1 V
lockin7265.gain = 20                    # Set AC gain to 20 dB
print(lockin7265.x)                     # Measure X channel voltage
lockin7265.shutdown()                   # Instrument shutdown

```
