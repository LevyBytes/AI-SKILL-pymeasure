# pymeasure.instruments.kuhneelectronic.Kusg245_250A.tune

[Owning PyMeasure class, adapter and connection contract](overview.md)

tune(*power*)

Search for and apply the frequency with the lowest reflection at the specified power.

Parameters:

**power** - power set-point used while tuning, in Watts, as an integer from 0 up to the constructor's `power_limit` parameter.
