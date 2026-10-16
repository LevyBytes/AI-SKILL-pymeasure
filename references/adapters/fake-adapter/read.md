# pymeasure.adapters.FakeAdapter.read

[Owning PyMeasure class, adapter and connection contract](overview.md)

read(***kwargs*)

Read either the whole read buffer or data up to, but not including, read_termination.

A subclass must not override this.

Parameters:

****kwargs** - Keyword arguments passed to the connection itself.

Returns str:

Instrument ASCII response, with read_termination excluded.

Return type:

`str`
