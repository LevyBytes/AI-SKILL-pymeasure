# pymeasure.instruments.oxfordinstruments.MercuryiTC

*class *pymeasure.instruments.oxfordinstruments.MercuryiTC(*adapter*, *name='Oxford MercuryiTC'*, ***kwargs*)

Provides a high-level interface for the Oxford Instruments Mercury iTC (Intelligent Temperature Controller). Its GPIB behavior is not fully SCPI-compliant; the only supported command is `*IDN?`. A Mercury iTC may use either a so-called SCPI instruction set, which is still not a true SCPI implementation, or a legacy instruction set. This implementation uses the so-called SCPI instruction set.

The iTC can be expanded with daughter boards for mixed temperature sensors, heaters, pressure sensors, cryogen level sensors, and auxiliary I/O. At present, this implementation covers only temperature sensors and heaters.

By default, one temperature sensor channel with Unique Identifier (`UID`) `'MB1.T1'` and one heater channel with UID `'MB0.H1'` are installed. Controller instantiation creates both channels automatically. They are available as `.TS_MB` and `.HTR_MB`, and also through the dictionary collections `.TS['MB1.T1']` and `.HTR['MB0.H1']`.

Additional daughter boards can host other sensors and heaters with specific `UID` values, for example `'DBX.T1'`, `'DBX.H1'` etc. After a MercuryiTC instance already exists, add them manually with `.add_temperature_sensor(UID)` and `.add_heater(UID)`. Use the correct UID reported by the Mercury iTC itself, because communication addresses channels by that UID. Access for these added channels is **only** through `.TS[UID]` and `.HTR[UID]`.

```python
from pymeasure.instruments.oxfordinstruments.mercuryitc import MercuryiTC

controller = MercuryiTC("GPIB::1")

# Print the current measured temperature of the motherboard temperature sensor aka 'MB1.T1'
print(controller.TS_MB.temperature)

# Print the motherboard temperature sensor control-loop setpoint
print(controller.TS['MB1.T1'].loop_T_setpoint)

# Add new temperature sensor with UID 'DB6.T1'
controller.add_temperature_sensor('DB6.T1')

# Print the new sensor's temperature
print(controller.TS['DBS.T1'].temperature)

```
