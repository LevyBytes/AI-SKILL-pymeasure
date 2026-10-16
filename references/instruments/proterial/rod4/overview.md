# pymeasure.instruments.proterial.ROD4

*class *pymeasure.instruments.proterial.ROD4(*adapter*, *name='ROD-4 MFC Controller'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Provides a high-level interface for the Proterial ROD-4(A) operator for mass flow controllers. The user must choose the channel to control (1-4).

```python
from pymeasure.instruments.proterial.rod4 import ROD4

rod4 = ROD4("ASRL1::INSTR")

print(rod4.version)             # Print version and series number
rod4.ch_1.mfc_range = 500       # Sets Channel 1 MFC range to 500 sccm
rod4.ch_2.valve_mode = 'flow'   # Sets Channel 2 MFC to flow control
rod4.ch_3.setpoint = 50         # Sets Channel 3 MFC to flow at 50% of full range
print(rod4.ch_4.actual_flow)    # Prints Channel 4 actual MFC flow in %

```
