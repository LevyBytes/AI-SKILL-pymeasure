# pymeasure.instruments.hp.hp856Xx.HP856Xx.normalize_trace_data_enabled

HP856Xx.normalize_trace_data_enabled

Control normalization for stimulus-response measurements. The function subtracts trace B from trace A, offsets the result by the normalized reference position value (`normalized_reference_level`), and shows the result in trace A. ‘normalize_trace_data_enabled’ is intended to be used with `store_open()` and `store_short()`, or with `store_thru()`. Those commands store a reference trace in trace B; consult their command descriptions for details. Normalization is accurate only when both the reference trace and measured trace are visible on-screen. If either trace is off-screen, the instrument displays an error. For ERR 903 A > DLMT, adjust range level (RL) to bring the measured response inside the analyzer display range. For ERR 904 B > DLMT, calibration is invalid and a thru or open/short calibration is required. When active (ON), the ‘normalize_trace_data’ command is automatically disabled by an instrument preset (IP) or at power on.

Type: `bool`
