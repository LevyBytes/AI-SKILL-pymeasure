# pymeasure.instruments.tcpowerconversion.CXN.read

[Owning PyMeasure class, adapter and connection contract](overview.md)

read()

Read a response message from the instrument.

By reading the message header, this method automatically determines the message length and verifies that the checksum is correct.

Returns:

the data fields

Return type:

bytes

Raises:

**ValueError** - raised when a checksum error is detected
