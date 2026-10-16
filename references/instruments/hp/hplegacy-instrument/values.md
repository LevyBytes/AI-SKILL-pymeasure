# pymeasure.instruments.hp.HPLegacyInstrument.values

[Owning PyMeasure class, adapter and connection contract](overview.md)

values(*command*, ***kwargs*)

Send a command to the instrument and return formatted response values as a list.

Parameters:

- **command** - SCPI command sent to the instrument.

- **preprocess_reply** - Optional callable that preprocesses the string received from the instrument before it is split. The callable returns that processed string.

- **separator** - Character used to split the device's returned string into a list. None uses any whitespace, as `str.split` does.

- **maxsplit** - Splits the device-returned string no more than maxsplit times. -1 (default) means unlimited splitting.

- **cast** –

Type used to cast each split-string element.

Deprecated since version 0.17.0: if casting fails, that element remains a string. A future version will raise an error instead. To allow mixed types explicitly, pass a dedicated function, for example `cast_or_str()` as the cast function.

- ****kwargs** - Keyword arguments forwarded to the `ask()` method.

Returns:

A list of the desired type, or (deprecated) str values where casting fails.
