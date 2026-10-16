# pymeasure.adapters.Adapter.read_bytes

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_bytes(*count=-1*, *break_on_termchar=False*, ***kwargs*)

Read the requested byte count from the instrument.

Subclass implementations must not replace this method.

Parameters:

- **count** (*int*) – Bytes requested for the read; -1 means use the complete read buffer.

- **break_on_termchar** (*bool*) – Stop the read when a termination character is encountered.

- ****kwargs** – Keyword arguments forwarded to the underlying connection.

Returns bytes:

Instrument byte response, including the termination bytes.

Return type:

`bytes`
