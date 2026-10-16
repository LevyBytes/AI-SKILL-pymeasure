# pymeasure.instruments.ami.AMI430

*class *pymeasure.instruments.ami.AMI430(*adapter*, *name='AMI superconducting magnet power supply.'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Provides a high-level interface for interacting with the AMI 430 Power supply.

```python
from pymeasure.instruments.ami.ami430 import AMI430

magnet = AMI430("TCPIP::web.address.com::7180::SOCKET")

magnet.coilconst = 1.182                 # kGauss/A
magnet.voltage_limit = 2.2               # Sets the voltage limit in V

magnet.target_current = 10               # Sets the target current to 10 A
magnet.target_field = 1                  # Sets target field to 1 kGauss

magnet.ramp_rate_current = 0.0357       # Sets the ramp rate in A/s
magnet.ramp_rate_field = 0.0422         # Sets the ramp rate in kGauss/s
magnet.ramp()                             # Initiates the ramping
magnet.pause()                            # Pauses the ramping
magnet.magnet_status                           # Returns the status of the magnet

magnet.ramp_to_current(5, rate=0.0357)             # Ramps the current to 5 A

magnet.shutdown()                     # Ramps the current to zero and disables output

```
