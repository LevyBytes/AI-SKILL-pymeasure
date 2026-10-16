# Read and set FSL parameters

First [connect the analyzer](network-connection.md) to provide the `fsl` object used below.

The driver exposes most settings as properties, so the same attribute-style access handles reads and writes. Bare numeric inputs are interpreted in base units (s, Hz, dB, …). Values may also include a unit suffix, for example `"1.5 GHz"` or `"1.5GHz"`. Reads always return numbers.

```pycon
>>> # Getting the current center frequency
>>> fsl.freq_center

9000000000.0

```

```python
# Changing it to 10 MHz by providing the numerical value
fsl.freq_center = 10e6

```

```pycon
>>> # Verifying:
>>> fsl.freq_center

10000000.0

```

```pycon
>>> # Changing it to 9 GHz by providing a string and verifying the result
>>> fsl.freq_center = '9GHz'
>>> fsl.freq_center

9000000000.0

```

```python
# Setting the span to maximum
fsl.freq_span = '7 GHz'

```
