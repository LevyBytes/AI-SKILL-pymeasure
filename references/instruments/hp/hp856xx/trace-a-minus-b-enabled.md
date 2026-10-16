# pymeasure.instruments.hp.hp856Xx.HP856Xx.trace_a_minus_b_enabled

HP856Xx.trace_a_minus_b_enabled

Control subtraction of trace B contents from trace A. In log mode, trace A receives the result in dBm. In linear mode, trace A receives the result in volts. When trace A is set to clear-write or max-hold mode, this operation continues. When AMB is enabled, an “M” appears on the left side of the display. `trace_a_minus_b_plus_dl` takes precedence over AMB.

Type: `bool`

Warning

Each displayed trace-element amplitude maps to one of 600 data points. The analyzer provides 10 points of overrange, corresponding to one-sixth of a division Kg of overrange. Results from trace addition or subtraction that exceed this boundary are clipped at the limit.
