# pymeasure.adapters.VISAAdapter.read

[Owning PyMeasure class, adapter and connection contract](overview.md)

read(***kwargs*)

Read until read_termination without including it, or consume the full read buffer.

Subclass implementations must not replace this method.

Parameters:

****kwargs** – Keyword arguments forwarded to the underlying connection.

Returns str:

Instrument reply decoded as ASCII, with read_termination omitted.

Return type:

`str`
