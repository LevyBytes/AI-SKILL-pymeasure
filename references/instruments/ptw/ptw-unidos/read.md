# pymeasure.instruments.ptw.ptwUNIDOS.read

[Owning PyMeasure class, adapter and connection contract](overview.md)

read()

Read the device response, then validate it for errors.

Returns:

`str` - String read with semicolons converted to comma

Raises:

*ValueError* on an error response, or *ConnectionError* when the error is unknown
