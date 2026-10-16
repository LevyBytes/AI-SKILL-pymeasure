# pymeasure.instruments.ametek.Ametek7270.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

Required for use by a property setter.

The Ametek protocol requires reading the default null character to verify that the property was set successfully. When the termination character is the Null character, the default read result becomes an empty string.
