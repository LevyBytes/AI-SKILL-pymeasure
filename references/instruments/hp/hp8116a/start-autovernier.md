# pymeasure.instruments.hp.HP8116A.start_autovernier

[Owning PyMeasure class, adapter and connection contract](overview.md)

start_autovernier(*control*, *digit*, *direction*, *start_value=None*)

Starts autovernier for the selected control.

Parameters:

- **control**: Control to modify, passed as `HP8116A.some_control`. Allowed controls are frequency, amplitude, offset, duty_cycle, and pulse_width

- **digit** - Digit to modify; type: `HP8116A.Digit`.

- **direction**: Direction used to modify the control; type: `HP8116A.Direction`.

- **start_value**: Optional starting value for autovernier. If omitted, the current value of the control is used. (default: `None`)

## Related property contracts

- Open when checking pymeasure.instruments.hp.HP8116A.status: [status](status.md).
