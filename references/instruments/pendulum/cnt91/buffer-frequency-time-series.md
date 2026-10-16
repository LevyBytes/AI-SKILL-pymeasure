# pymeasure.instruments.pendulum.cnt91.CNT91.buffer_frequency_time_series

[Owning PyMeasure class, adapter and connection contract](overview.md)

buffer_frequency_time_series(*channel*, *n_samples*, *sample_rate=None*, *gate_time=None*, *trigger_source=None*, *back_to_back=True*)

Capture a time series into the buffer, then read it once the operation completes.

Parameters:

- **channel** – Channel to use

- **n_samples** – Count of samples

- **gate_time** – Measurement gate duration in s (default: `None`)

- **trigger_source** – Optional trigger source used to start the measurement (default: `None`)

- **back_to_back** – When True, run the buffer measurement back-to-back. (default: `True`)

- **sample_rate** –

Sample rate in Hz

Deprecated since version 0.14: Use gate_time as the replacement parameter. (default: `None`)
