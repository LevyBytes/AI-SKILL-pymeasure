# pymeasure.generator.Generator.instantiate

[Owning PyMeasure class, adapter and connection contract](overview.md)

instantiate(*instrument_class*, *adapter*, *manufacturer*, *adapter_kwargs=None*, ***kwargs*)

Create the instrument and record the communication used during instantiation.

..note:

You have to give all keyword arguments necessary for adapter instantiation in
`adapter_kwargs`, even those, which are defined somewhere in the instrument's
``__init__`` method, be it as a default value, be it directly in the
``Instrument.__init__()`` call.

Parameters:

- **instrument_class** - Instrument class to test.

- **adapter** - Adapter, either an instance or str, used for instrument instantiation.

- **manufacturer** - Module from which the instrument is imported, e.g. 'hcp' when instrument_class is 'pymeasure.hcp.tc038'.

- **adapter_kwargs** - Keyword arguments used for adapter instantiation (see note above). (default: `None`)

- ****kwargs** - Keyword arguments for the instrument instantiation.

Returns:

A man-in-the-middle instrument usable like a normal instrument.
