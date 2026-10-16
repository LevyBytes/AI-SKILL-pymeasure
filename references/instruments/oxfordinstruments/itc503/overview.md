# pymeasure.instruments.oxfordinstruments.ITC503

*class *pymeasure.instruments.oxfordinstruments.ITC503(*adapter*, *name='Oxford ITC503'*, *clear_buffer=True*, *min_temperature=0*, *max_temperature=1677.7*, ***kwargs*)

Bases: [`OxfordInstrumentsBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/base.html#pymeasure.instruments.oxfordinstruments.base.OxfordInstrumentsBase)

Models the Oxford Intelligent Temperature Controller 503.

```python
from pymeasure.instruments.oxfordinstruments.itc503 import ITC503

itc = ITC503("GPIB::24")        # Default channel for the ITC503

itc.control_mode = "RU"         # Set the control mode to remote
itc.heater_gas_mode = "AUTO"    # Turn on auto heater and flow
itc.auto_pid = True             # Turn on auto-pid

print(itc.temperature_setpoint) # Print the current set-point
itc.temperature_setpoint = 300  # Change the set-point to 300 K
itc.wait_for_temperature()      # Wait for the temperature to stabilize
print(itc.temperature_1)        # Print the temperature at sensor 1

```
