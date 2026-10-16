# pymeasure.instruments.hp.hp856Xx.HP856Xx.deactivate_marker

HP856Xx.deactivate_marker(*all_markers=False*)

Deactivate the active marker, or deactivate every marker when requested.

Parameters:

**all_markers** (*bool*) – If `True`, all markers are deactivated; if false, only the active marker is turned off (optional) (default: `False`)

```python
# place first marker at 300 MHz
instr.marker_frequency = 300e6

# place second marker 2 MHz apart from first
instr.marker_delta = 2e6

# deactivate active marker (delta marker)
instr.deactivate_marker()

# deactivate all markers
instr.deactivate_marker(all_markers=True)

```
