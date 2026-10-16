# pymeasure.instruments.hp.hp856Xx.HP856Xx.recall_open_short_average

HP856Xx.recall_open_short_average()

Load the internally stored open/short average reference trace into trace B. The analyzer also restores the saved open/short reference state.

```python
from pymeasure.instruments.hp.hp856Xx import SweepCoupleMode

instr.preset()
instr.sweep_single()
instr.start_frequency = 300e3
instr.stop_frequency = 1e9

instr.source_power_enabled = True
instr.sweep_couple = SweepCoupleMode.StimulusResponse
instr.source_peak_tracking()

input("CONNECT OPEN. PRESS CONTINUE WHEN READY TO STORE.")
instr.trigger_sweep()
instr.done()
instr.store_open()

input("CONNECT SHORT. PRESS CONTINUE WHEN READY TO STORE AND AVERAGE.")
instr.trigger_sweep()
instr.done()
instr.store_short()

input("RECONNECT DUT. PRESS CONTINUE WHEN READY.")
instr.trigger_sweep()
instr.done()

instr.normalize = True

instr.trigger_sweep()
instr.done()

instr.normalized_reference_position = 8
instr.trigger_sweep()

instr.preset()
# demonstrate recall of open/short average trace
instr.recall_open_short_average()
instr.trigger_sweep()

```
