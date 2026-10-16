# pymeasure.instruments.tcpowerconversion.CXN.values

[Owning PyMeasure class, adapter and connection contract](overview.md)

values(*command*, *cast=<class 'int'>*, *separator='*, *'*, *preprocess_reply=None*, ***kwargs*)

Send the instrument a command and return the result as a list of formatted values.

This method is derived from CommonBase.values and adapted for bytes communication messages here, with no str conversion and strip. The implementation is general so both PresetChannel and CXN can use it. See Github issue #784 for details.

Parameters:

- **command** - SCPI command sent to the instrument

- **separator** - separator character for splitting the string into a list (default: `','`)

- **cast** - type used to cast the result (default: `<class 'int'>`)

- **preprocess_reply** - optional callable that processes instrument values before casting. It returns the processed string. (default: `None`)

Returns:

Returns a list in the desired type, with strings kept where casting fails
