# Command Translation

Alphabetized mapping from implemented B1500 commands to the driver method or attribute that handles each command.

| Command | Property/Method |
| --- | --- |
| `AAD` | `SMU.adc_type` |
| `AB` | `abort()` |
| `AIT` | `adc_setup()` |
| `AV` | `adc_averaging()` |
| `AZ` | `adc_auto_zero` |
| `BC` | `clear_buffer()` |
| `CL` | `SMU.disable()` |
| `CM` | `auto_calibration` |
| `CMM` | `SMU.meas_op_mode` |
| `CN` | `SMU.enable()` |
| `DI` | `SMU.force()` mode: `'CURRENT'` |
| `DV` | `SMU.force()` mode: `'VOLTAGE'` |
| `DZ` | `force_gnd()`, `SMU.force_gnd()` |
| `ERRX?` | `check_errors()` |
| `FL` | `SMU.filter` |
| `FMT` | `data_format()` |
| `*IDN?` | `id` |
| `*LRN?` | `query_learn()`, plus several helpers that retrieve settings and format them directly |
| `MI` | `SMU.sampling_source()` mode: `'CURRENT'` |
| `ML` | `sampling_mode` |
| `MM` | `meas_mode()` |
| `MSC` | `sampling_auto_abort()` |
| `MT` | `sampling_timing()` |
| `MV` | `SMU.sampling_source()` mode: `'VOLTAGE'` |
| `*OPC?` | `check_idle()` |
| `PA` | `pause()` |
| `PAD` | `parallel_meas` |
| `RI` | `meas_range_current` |
| `RM` | `SMU.meas_range_current_auto()` |
| `*RST` | `reset()` |
| `RV` | `meas_range_voltage` |
| `SSR` | `series_resistor` |
| `TSC` | `time_stamp` |
| `TSR` | `clear_timer()` |
| `UNT?` | `query_modules()` |
| `WAT` | `wait_time()` |
| `WI` | `SMU.staircase_sweep_source()` mode: `'CURRENT'` |
| `WM` | `sweep_auto_abort()` |
| `WSI` | `SMU.synchronous_sweep_source()` mode: `'CURRENT'` |
| `WSV` | `SMU.synchronous_sweep_source()` mode: `'VOLTAGE'` |
| `WT` | `sweep_timing()` |
| `WV` | `SMU.staircase_sweep_source()` mode: `'VOLTAGE'` |
| `XE` | `send_trigger()` |

### Examples
