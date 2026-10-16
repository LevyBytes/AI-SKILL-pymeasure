# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.sweep_delay_time

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *sweep_delay_time*: Any*

Use `GDLY` to set Ta for sweep delay, or Ta for generation/delay timing, on the master/slave channels in delayed sweep and synchronous pulse measurement operation.

Type:

float

Note

If the sweep delay time violates the required relationship (Ta<Tw and Ta<Td+Tit), an execution error is raised and the value is not set:

Tw: Pulse width Td: Major delay time Tit: Integration time

## Related property contracts

- Open when checking pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.operation_mode: [operation_mode](operation-mode.md).
