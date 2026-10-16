# pymeasure.instruments.inficon.sqm160.SQM160.read

[Owning PyMeasure class, adapter and connection contract](overview.md)

read()

Read a response message from the instrument.

This method also validates the checksum.

Returns:

the response packet

Return type:

string

Raises:

**ConnectionError** - raised when a checksum error or incorrect response status is detected.
