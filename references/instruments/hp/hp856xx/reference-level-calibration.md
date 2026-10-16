# pymeasure.instruments.hp.hp856Xx.HP856Xx.reference_level_calibration

HP856Xx.reference_level_calibration

Set or read remote reference-level calibration. To calibrate the reference level, route the 300 MHz calibration signal to the RF input. Use center frequency 300 MHz, frequency span 20 MHz, and reference level -10 dBm. Run the RLCAL command to shift the input signal to the reference level. Calibration is correct when the signal peak is directly on the reference-level line. The resulting value can be stored in analyzer EEROM only from the front panel. Querying the RLCAL command returns the current value.

Type: `float`

```python
from pymeasure.instruments.hp.hp856Xx import AmplitudeUnits, PeakSearchMode

# connect cal signal to rf input
instr.preset()
instr.amplitude_unit = AmplitudeUnits.DBM
instr.center_frequency = 300e6
instr.span = 100e3
instr.reference_level = 0
instr.trigger_sweep()

instr.peak_search(PeakSearchMode.High)
level = instr.marker_amplitude
rlcal = instr.reference_level_calibration - int((level + 10) / 0.17)
instr.reference_level_calibration = rlcal

```
