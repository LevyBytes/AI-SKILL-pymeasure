# pymeasure.instruments.Instrument

*class *pymeasure.instruments.Instrument(*adapter*, *name*, *includeSCPI=None*, ***kwargs*)

Superclass used for every Instrument definition.

Communication with the connected hardware device is handled through one of the [`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter) classes. That separation keeps the instrument and command definitions independent from the communication interface selected.

If `adapter` is a string, it is interpreted as a suitable resource name. Depending on the installed VISA library, the value may be a simple name like `COM1` or `ASRL2`, or a more complex [VISA resource name](https://pyvisa.readthedocs.io/en/latest/introduction/names.html) that identifies the connection target.

If `adapter` is an integer, it is converted into a GPIB resource name. For both string and integer inputs, a [`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter) is created from that resource name. Keyword arguments may further configure the connection.

For any other input, the supplied [`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter) object is used directly and keyword arguments are ignored.

By default, this class includes basic SCPI commands. Instruments that do not support the standard SCPI commands can turn that behavior off with `includeSCPI`.

Parameters:

- **adapter** (`Union`[[`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter), `int`, `str`]) - String, integer, or [`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter) subclass object.

- **name** (*string*) - Instrument name, often defaulting to the model designation.

- **includeSCPI** (`Optional`[`bool`]) –

Required boolean controlling whether standard SCPI commands are included.

Deprecated since version 0.14: When this is True, inherit from [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin) instead. (default: `None`)

- ****kwargs** - When `adapter` is a string or integer, additional arguments are forwarded to [`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter); see that class for details. They are discarded for other adapter forms.
