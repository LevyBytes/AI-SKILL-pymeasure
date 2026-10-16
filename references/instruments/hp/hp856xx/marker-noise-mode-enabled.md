# pymeasure.instruments.hp.hp856Xx.HP856Xx.marker_noise_mode_enabled

HP856Xx.marker_noise_mode_enabled

Control the detector mode that samples and averages 32 data points: 16 points before the marker, the marker point, and 15 points after it. The average is compensated for log or linear amplifier behavior, bandwidth shape factor, IF detector response, and resolution bandwidth. If two markers are enabled, either in ‘marker_delta’ mode or 1/marker delta mode, ‘marker_noise_mode_enabled’ applies to the active marker rather than the anchor marker. This supports direct signal-to-noise density measurement. Query the result with the ‘marker_amplitude’ command.

Type: `bool`

```python
# activate signal-to-noise density mode
instr.marker_noise_mode_enabled = True

# get noise density by `marker_amplitude`
print("Signal-to-noise density: %d dbm / Hz" % instr.marker_amplitude)

```
