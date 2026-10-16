# pymeasure.instruments.tdk.tdk_gen40_38.TDK_Gen40_38

Covers: TDK Lambda Genesys 40-38 DC power supply; TDK Lambda Genesys 80-65 DC power supply; TDK Lambda.

## TDK Lambda Genesys 40-38 DC power supply

### TDK Lambda Genesys 40-38 DC power supply

 *class *pymeasure.instruments.tdk.tdk_gen40_38.TDK_Gen40_38(*adapter*, *name='TDK Lambda Gen40-38'*, *address=6*, ***kwargs*)

Bases: `TDK_Lambda_Base`

Models the TDK Lambda Genesys 40-38 DC power supply. Its commands come from the TDK_Lambda_Base parent class, and dynamic properties constrain the allowed values for selected properties.

```python
from pymeasure.instruments.tdk.tdk_gen40_38 import TDK_Gen40_38

psu = TDK_Gen40_38("COM3", 6)       # COM port and daisy-chain address
psu.remote = "REM"                  # PSU in remote mode
psu.output_enabled = True           # Turn on output
psu.ramp_to_current(2.0)            # Ramp to 2.0 A of current
print(psu.current)                  # Measure actual PSU current
print(psu.voltage)                  # Measure actual PSU voltage
psu.shutdown()                      # Run shutdown command

```

To initialize a TDK instrument, supply the current TDK power supply address. For TDK Lambda, the default address is 6.

Parameters:

- **adapter** – VISAAdapter instance

- **name** – Instrument name; default value is “TDK Lambda Gen40-38” (default: `'TDK Lambda Gen40-38'`)

- **address** – Serial port daisy chain number; default value is 6. (default: `6`)
