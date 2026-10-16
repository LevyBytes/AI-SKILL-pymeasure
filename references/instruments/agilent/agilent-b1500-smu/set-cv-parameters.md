# pymeasure.instruments.agilent.agilentB1500.SMU.set_cv_parameters

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_cv_parameters(*mode*, *start*, *stop*, *steps*, *comp=None*)

Configure mode and sweep parameters for `MeasMode.CV_SWEEP` measurement. (`WDCV`)

Parameters:

- **mode** (`SweepMode`) – Sweep mode

- **start** (`float`) – Starting voltage for the sweep in V

- **stop** (`float`) – Ending voltage for the sweep in V

- **steps** (`int`) – Staircase sweep step count

- **comp** (`Optional`[`float`]) – Compliance current in A. If not provided, the existing value remains in use. (default: `None`)

Return type:

`None`
