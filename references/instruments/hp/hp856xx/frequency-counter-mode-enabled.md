# pymeasure.instruments.hp.hp856Xx.HP856Xx.frequency_counter_mode_enabled

HP856Xx.frequency_counter_mode_enabled

Enable frequency counter mode for the active marker frequency, or for the frequency difference between two markers. If there is no active marker, ‘frequency_counter_mode_enabled’ creates one at the trace center and counts that marker frequency. The frequency counter improves frequency readout accuracy by stopping at the marker, counting, and then resuming the sweep. Use ‘frequency_counter_resolution’ to set the counter resolution. Use ‘marker_frequency’ to read back the counter value.

```python
instr.frequency_counter_mode_enabled = True

```
