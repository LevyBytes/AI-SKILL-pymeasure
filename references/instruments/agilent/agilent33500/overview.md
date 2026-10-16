# pymeasure.instruments.agilent.Agilent33500

*class *pymeasure.instruments.agilent.Agilent33500(*adapter*, *name='Agilent 33500 Function/Arbitrary Waveform generator family'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Agilent 33500 Function/Arbitrary Waveform Generator family.

Subclasses model the individual instruments. A channel may be supplied for control; when it is omitted, the driver chooses a device-specific default. For example, Agilent33500B uses channel 1. Consult the reference manual for your device.

```python
from pymeasure.instruments.agilent.agilent33500 import Agilent33500

generator = Agilent33500("GPIB::1")

generator.shape = 'SIN'                 # Sets default channel output signal shape to sine
generator.channels[1].shape = 'SIN'           # Sets channel 1 output signal shape to sine
generator.frequency = 1e3               # Sets default channel output frequency to 1 kHz
generator.channels[1].frequency = 1e3         # Sets channel 1 output frequency to 1 kHz
generator.channels[2].amplitude = 5           # Sets channel 2 output amplitude to 5 Vpp
generator.channels[2].output = 'on'           # Enables channel 2 output

generator.channels[1].shape = 'ARB'           # Set channel 1 shape to arbitrary
generator.channels[1].arb_srate = 1e6         # Set channel 1 sample rate to 1MSa/s

generator.channels[1].data_volatile_clear()   # Clear channel 1 volatile internal memory
generator.channels[1].data_arb(               # Send data of arbitrary waveform to channel 1
    'test',
    range(-10000, 10000, +20),          # In this case a simple ramp
    data_format='DAC'                   # Data format is set to 'DAC'
 )
generator.channels[1].arb_file = 'test'       # Select the transmitted waveform 'test'

```
