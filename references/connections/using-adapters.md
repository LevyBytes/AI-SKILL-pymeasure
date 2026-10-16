# Using adapters

Adapters handle communication with the hardware underneath. In the earlier example, constructing the instrument with the string GPIB::4 creates a VISAAdapter by default, the most common default adapter, and connects through VISA. Supplying a string (or, for GPIB, an integer) is the overwhelmingly common pattern for creating pymeasure instruments.

For cases outside the standard setup, you can pass an adapter object rather than passing a string.

```python
from pymeasure.adapters import VISAAdapter

adapter = VISAAdapter("GPIB::4")
sourcemeter = Keithely2400(adapter)

```

To use a Prologix GPIB device on `/dev/ttyUSB0` instead, build the adapter in the same general manner; Linux requires the proper permissions, as noted for [`PrologixAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.PrologixAdapter). Many instruments can share one Prologix adapter. Because of that, an existing instance can be used to generate new [`PrologixAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.PrologixAdapter) instances for different GPIB addresses.

```python
from pymeasure.instruments.keithley.keithley2000 import Keithley2000
from pymeasure.instruments.keithley.keithley2400 import Keithley2400

from pymeasure.adapters import PrologixAdapter

adapter = PrologixAdapter('ASRL/dev/ttyUSB0::INSTR', address=7)
sourcemeter = Keithley2400(adapter)  # at GPIB address 7
multimeter = Keithley2000(adapter.gpib(9))  # at GPIB address 9

```
