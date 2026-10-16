# pymeasure.instruments.hp.hp856Xx.HP856Xx.sweep_time

HP856Xx.sweep_time

Control sweep time. This function is normally coupled, so the instrument automatically chooses the optimum value permitted by the current settings. A sweep time may also be specified manually. If the requested sweep time is too fast for the current setup, calibration is lost and the display shows ‘MEAS UNCAL’. Sweep time cannot be changed when resolution bandwidth is 10 Hz, 30 Hz, or 100 Hz.

Type: `str, float`

Accepts real values from 50E—3 to 100 when span is greater than 0 Hz, and from 50E—6 to 60 when span equals 0 Hz. When resolution bandwidth is <100 Hz, sweep time is not adjustable.
