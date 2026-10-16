# pymeasure.instruments.hp.hp856Xx.HP856Xx.get_power_bandwidth

HP856Xx.get_power_bandwidth(*trace*, *percent*)

Measure total power across all signal responses in a trace array, then calculate the bandwidth corresponding to a requested percentage of that total power. For example, specifying 100% makes the power bandwidth equal the current frequency span. Specifying 50% removes trace elements from both array ends until the remaining trace elements contain half of the computed total power. The controller receives the frequency span for those remaining trace elements as the power bandwidth.

Parameters:

- **trace** (*str*) – Trace selection, either from `Trace` or ‘TRA’ for Trace A or ‘TRB’ for Trace B

- **percent** (*float*) – Percentage of total power, 0 … 100 %

```python
# reset spectrum analyzer
instr.preset()

# set to single sweep mode
instr.sweep_single()

instr.center_frequency = 300e6
instr.span = 1e6

instr.maximum_hold()

instr.trigger_sweep()

if instr.done:
    pbw = instr.power_bandwidth(Trace.A, 99.0)
    print("The power bandwidth at 99 percent is %f kHz" % (pbw / 1e3))

```
