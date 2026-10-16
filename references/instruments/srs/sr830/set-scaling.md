# pymeasure.instruments.srs.SR830.set_scaling

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_scaling(*channel*, *percent*, *expand=0*, *precent=None*)

Set a channel offset, where X=1, Y=2, R=3, to a chosen percent (-105% to 105%) of the signal, optionally using expansion term 0, 10=1, 100=2. :rtype: `None`

Deprecated since version 0.17.0: the `precent` parameter is deprecated; use `percent` for the same behavior.
