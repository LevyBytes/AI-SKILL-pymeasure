# FSL markers

First [connect the analyzer](network-connection.md) to provide the `fsl` object used below.

Markers use a separate class. Instantiate one with:

```python
m1 = fsl.create_marker()

```

Set peak excursion:

```python
m1.peak_excursion = 3

```

Move the marker to an exact position:

```python
m1.x = 10e9

```

Search leftward for the next peak, then read its level:

```pycon
>>> m1.to_next_peak('left')
>>> m1.y

-34.9349060059

```
