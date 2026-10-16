# pymeasure.instruments.agilent.agilentB1500.CMU.set_cv_timings

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_cv_timings(*hold_time*, *delay_time*, *step_delay_time=0.0*, *step_source_trigger_delay_time=0.0*)

Configure timing for `MeasMode.CV_SWEEP` measurement. (`WTDCV`)

Parameters:

- **hold_time** (`float`) - In seconds, the wait after measurement start before delay time begins for the first step.

- **delay_time** (`float`) - In seconds, the wait after step output forcing begins before step measurement starts.

- **step_delay_time** (`float`) –

In seconds, the wait after a step measurement starts before the next step output starts being forced.

When step_delay_time is less than the measurement time, B1500 waits for measurement completion before forcing the next step output. (default: `0.0`)

- **step_source_trigger_delay_time** (`float`) - In seconds, the wait after step output setup finishes before a step output setup completion trigger is sent. (default: `0.0`)

Return type:

`None`
