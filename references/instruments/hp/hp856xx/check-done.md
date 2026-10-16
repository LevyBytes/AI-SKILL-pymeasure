# pymeasure.instruments.hp.hp856Xx.HP856Xx.check_done

HP856Xx.check_done()

Wait until every command entered before :meth:’check_done’ in the command string has finished. Sending `trigger_sweep()` before ‘check_done’ makes the spectrum analyzer finish a complete sweep before the program proceeds. With very long sweep times, the adapter may raise a timeout error before the spectrum analyzer finishes, depending on the timeout.

```python
instr.trigger_sweep()

# wait for a full sweep and than 'do_something'
instr.check_done()
do_something()

```
