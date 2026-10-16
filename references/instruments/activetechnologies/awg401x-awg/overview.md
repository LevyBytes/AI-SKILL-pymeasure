# pymeasure.instruments.activetechnologies.AWG401x_AWG

*class *pymeasure.instruments.activetechnologies.AWG401x_AWG(*adapter*, ***kwargs*)

Bases: `AWG401x_base`

Models the Active Technologies AWG-401x Arbitrary Waveform Generator when it is operating in AWG mode.

```python
from pymeasure.instruments.activetechnologies.AWG401x import AWG401x_AWG

wfg = AWG401x_AWG("TCPIP::192.168.0.123::INSTR")

wfg.reset()             # Reset the instrument at default state

# Set a oscillating waveform
wfg.waveforms["MyWaveform"] = [1, 0] * 8

for i in range(1, wfg.num_ch + 1):
    wfg.entries[1].channels[i].voltage_high = 1       # Sets high voltage = 1
    wfg.entries[1].channels[i].voltage_low = 0        # Sets low voltage = 1
    wfg.entries[1].channels[i].waveform = "SQUARE"    # Sets a square wave
    wfg.setting_ch[i].enabled = True            # Enable channel

wfg.entries.resize(2)           # Resize the number of entries to 2

wfg.entries[2].channels[1].waveform = "MyWaveform"   # Set custom waveform

wfg.enabled = True              # Enable output of waveform generator
wfg.beep()                      # "beep"

print(wfg.check_errors())       # Get the error queue

```
