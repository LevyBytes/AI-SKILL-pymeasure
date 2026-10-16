# pymeasure.adapters.VISAAdapter.write_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

write_bytes(*content*, ***kwargs*)

Send raw bytes content to the instrument.

Subclass implementations must not replace this method.

Parameters:

- **content** (*bytes*) – Bytes content sent to the instrument.

- ****kwargs** – Keyword arguments forwarded to the underlying connection.

Return type:

`None`
