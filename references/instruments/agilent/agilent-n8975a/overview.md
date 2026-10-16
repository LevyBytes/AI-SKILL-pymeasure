# pymeasure.instruments.agilent.AgilentN8975A

*class *pymeasure.instruments.agilent.AgilentN8975A(*adapter*, *name='Agilent N8975A'*, *timeout=5000*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for the Agilent N8975A Noise Figure Analyzer.

```python
from pymeasure.instruments.agilent.agilentN8975A import AgilentN8975A

nfa = AgilentN8975A("GPIB0::16::INSTR")
nfa.adapter.connection.timeout = 30000  # set a new timeout to 30 sec
nfa.abort()  # abort all running measurements
nfa.single()  # perform a single sweep measurement
nfa.complete
noise_figure = nfa.noise_figure_db  # get the noise figure data
gain = nfa.gain_db  # get the gain data

```
