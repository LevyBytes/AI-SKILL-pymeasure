# pymeasure.instruments.thyracont.smartline_v1.SmartlineV1.read

[Owning PyMeasure class, adapter and connection contract](overview.md)

read()

Read one response message from the instrument.

The method verifies that the checksum is correct as well.

Returns:

the data fields

Return type:

string

Raises:

**ValueError** – raised when a checksum error is found
