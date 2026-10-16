# pymeasure.instruments.hp.hp856Xx.HP856Xx.trace_a_minus_b_plus_dl_enabled

HP856Xx.trace_a_minus_b_plus_dl_enabled

Control the function that subtracts trace B from trace A, then adds the display line. In log mode, the result is stored in trace A as dBm. In linear mode, trace A stores the value in volts. When trace A is set to clear-write or max-hold mode, the operation keeps running automatically. While the function is active, an “M” is shown on the left side of the display.

Type: `bool`

Warning

Each displayed trace-element amplitude maps to one of 600 data points. The analyzer provides 10 points of overrange, corresponding to one-sixth of a division Kg of overrange. Results from trace addition or subtraction that exceed this boundary are clipped at the limit.
