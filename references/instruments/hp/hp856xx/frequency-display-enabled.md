# pymeasure.instruments.hp.hp856Xx.HP856Xx.frequency_display_enabled

HP856Xx.frequency_display_enabled

Return whether the frequency-related annotations are displayed. It returns ‘False’ when none are visible and ‘True’ otherwise. This covers start and stop frequencies, center frequency, frequency span, marker readouts, center frequency step-size, and signal identification to center frequency. Query the spectrum analyzer to retrieve the frequency data.

Type: `bool`

```python
if instr.frequency_display:
    print("Frequencies get displayed")

```
