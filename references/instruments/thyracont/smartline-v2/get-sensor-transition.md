# pymeasure.instruments.thyracont.smartline_v2.SmartlineV2.get_sensor_transition

[Owning PyMeasure class, adapter and connection contract](overview.md)

get_sensor_transition()

Read the active sensor transition between sensors.

return interpretation:

- direct

switch at 1 mbar.

- continuous

switch between 5 and 15 mbar.

- F[float]T[float]

switch between the low value and the high value.

- D[float]

switch at value.
