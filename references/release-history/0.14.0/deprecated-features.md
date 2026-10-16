# Version 0.14.0 (2024-05-22) — Deprecated features

- `TelnetAdapter` was removed because its library is deprecated (@BenediktBurger, #1045).

- `ManagedWindowBase` now uses `enable_file_input` instead of the `directory_input` keyword argument (@CasperSchippers, #964).

- All instruments must now provide the `includeSCPI` parameter, including instruments that use SCPI (@BenediktBurger, #1007).

- Using includeSCPI=True is deprecated; devices with SCPI command support should inherit from `SCPIMixin`.

- `LakeShoreTemperatureChannel` now uses `celsius` instead of the `celcius` attribute (@afuetterer, #1003).

- For Keithley instruments, the `error` property was replaced with `next_error`.

- Pendulum CNT-91 now uses `gate_time` instead of the `measurement_time` property.

- For Pendulum CNT-91, the `buffer_frequency_time_series` keyword argument `sample_rate` was replaced with `gate_time`.

- MKS937B `unit` now uses `instruments/mksinst/mks937b/Unit` rather than strings (@dkriegner, @BenediktBurger #1034).
