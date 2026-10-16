# pymeasure.instruments.agilent.agilentB1500.CMU.set_cv_parameters

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_cv_parameters(*mode*, *start*, *stop*, *steps*)

Configure mode and sweep settings for `MeasMode.CV_SWEEP` measurement. (`WDCV`)

Parameters:

- **mode** (`SweepMode`) – Sweep mode

- **start** (`float`) - Start voltage for the sweep in V

- **stop** (`float`) - Stop voltage for the sweep in V

- **steps** (`int`) - Staircase sweep step count

Return type:

`None`
