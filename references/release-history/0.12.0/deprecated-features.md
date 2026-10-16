# Version 0.12.0 (2023-07-05) — Deprecated features

- For HP 34401A, the `voltage_ac`, `current_dc`, `current_ac`, `resistance`, and `resistance_4w` properties should be replaced by `function_` and `reading`.

- For Toptica IBeamSmart, replace `channel1_enabled` with the `ch_1.enabled` property, with the same pattern for channel2. `laser_enabled` is also deprecated; use `emission` instead (@bmoneke, #819).

- For TelnetAdapter, use `VISAAdapter` instead because VISA supports TCPIP connections. Connect to a server with resource_name `TCPIP[board]::<hostname>::<port>::SOCKET` (@Max-Herbold, #835).

- For Attocube ANC300, replace the `host` argument by passing a resource string or adapter as `Adapter` to `Instrument`. Communication now uses `VISAAdapter` instead of deprecated `TelnetAdapter`. The initializer accepts `name` as its second keyword argument, so earlier positional initialization arguments such as axisnames, passwd, and query_delay should become keyword arguments.

- The property creators `control`, `measurement`, and `setting` no longer accept arbitrary keyword arguments. Use `v_kwargs` for arguments that should be forwarded to the `values` method.

- The property creators `control`, `measurement`, and `setting` no longer accept command_process. Use either a dynamic property or a Channel, depending on the case (@bmoneke, #878).

- See also the next section.
