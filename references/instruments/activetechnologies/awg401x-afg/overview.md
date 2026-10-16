# pymeasure.instruments.activetechnologies.AWG401x_AFG

*class *pymeasure.instruments.activetechnologies.AWG401x_AFG(*adapter*, ***kwargs*)

Bases: `AWG401x_base`

Models the Active Technologies AWG-401x Arbitrary Waveform Generator when it is operating in AFG mode.

```python
from pymeasure.instruments.activetechnologies.AWG401x import AWG401x_AFG

wfg = AWG401x_AFG("TCPIP::192.168.0.123::INSTR")

wfg.reset()                     # Reset the instrument at default state

wfg.channels[1].shape = "SINUSOID"    # Sets a sine waveform on CH1
wfg.channels[1].frequency = 4.7e3     # Sets the frequency to 4.7 kHz on CH1
wfg.channels[1].amplitude = 1         # Set amplitude of 1 V on CH1
wfg.channels[1].offset = 0            # Set the amplitude to 0 V on CH1
wfg.channels[1].enabled = True        # Enables the CH1

wfg.channels[2].shape = "SQUARE"      # Sets a square waveform on CH2
wfg.channels[2].frequency = 100e6     # Sets the frequency to 100 MHz on CH2
wfg.channels[2].amplitude = 0.5         # Set amplitude of 0.5 V on CH2
wfg.channels[2].offset = 0            # Set the amplitude to 0 V on CH2
wfg.channels[2].enabled = True        # Enables the CH2

wfg.enabled = True              # Enable output of waveform generator
wfg.beep()                      # "beep"

print(wfg.check_errors())       # Get the error queue

```
