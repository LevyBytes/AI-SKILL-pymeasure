# pymeasure.instruments.kuhneelectronic.Kusg245_250A

*class *pymeasure.instruments.kuhneelectronic.Kusg245_250A(*adapter*, *name='KU SG 2.45 250 A'*, *power_limit=250*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

High-level interface for operating the KU SG 2.45 250 A - 2.45 GHz ISM-Band Microwave Generator.

Parameters:

**power_limit** - maximum allowed power set-point in Watts, as an integer from 0 to 250. See `power_setpoint` and `tune()`. (default: `250`)

Usage example:

```python
from pymeasure.instruments.kuhneelectronic import Kusg245_250A

generator = Kusg245_250A("ASRL3::INSTR", power_limit=100) # limits the output
                                                          # power set-point to 100 W

generator.external_enabled = False      # biasing and RF output controlled by serial comm
generator.power = 20                    # Sets the output power to 20 Watts
generator.bias_enabled = True           # Enables amplifier biasing
generator.rf_enabled = True             # Enables the RF output

p_fwd = generator.power_forward         # Reads forward power in Watts
p_rev = generator.power_reverse         # Reads reflected power in Watts

```

## Related property contracts

- Open when checking pymeasure.instruments.kuhneelectronic.Kusg245_250A.bias_enabled: [bias_enabled](bias-enabled.md).
