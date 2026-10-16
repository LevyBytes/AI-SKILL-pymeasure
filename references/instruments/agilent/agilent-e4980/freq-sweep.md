# pymeasure.instruments.agilent.AgilentE4980.freq_sweep

[Owning PyMeasure class, adapter and connection contract](overview.md)

freq_sweep(*freq_list*, *return_freq=False*)

Execute a frequency-list sweep with sequential triggering.

Parameters:

- **freq_list** – list of frequencies

- **return_freq** - when True, include the frequency values reported by the instrument in the return data (default: `False`).

Returned measurements follow the active `mode` configuration.
