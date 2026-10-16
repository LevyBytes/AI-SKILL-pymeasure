# pymeasure.instruments.teledyne.TeledyneMAUI.vbs_ask

[Owning PyMeasure class, adapter and connection contract](overview.md)

vbs_ask(*name*)

Return a VBS variable's value.

Only target must be supplied; this method builds the query. Note: the target name is not escaped!

See `vbs_write()` for additional detail.

Minimal usage example:

```python
instrument.vbs_ask("app.Display.GridMode")

```

Return type:

`str`
