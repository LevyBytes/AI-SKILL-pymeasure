# pymeasure.instruments.keysight.Keysight81160A.setting

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *setting(*set_command*, *docs*, *validator=<function CommonBase.&lt;lambda&gt;>*, *values=()*, *map_values=False*, *set_process=<function CommonBase.&lt;lambda&gt;>*, *check_set_errors=False*, *dynamic=False*)

Create a class property from the supplied commands. This property can be set, but attempting to read it from the instrument raises an exception.

Parameters:

- **set_command** (`str`) – String command that writes the value

- **docs** (`str`) – Docstring text inserted into the documentation

- **validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `Any`]) – Function that receives a value plus valid values and returns an accepted value; otherwise it raises an exception (default: `<function CommonBase.<lambda> at 0x7aa5aa7f87d0>`)

- **values** (`TypeVar`(`Vs`)) – Valid values supplied as a list, tuple, range, or dictionary; when `map_values` is True this may also map values. (default: `()`)

- **map_values** (`bool`) – Boolean flag selecting whether values are treated as a map (default: `False`)

- **set_process** (`Callable`[[`Any`], `Any`]) – Function that receives a value, can transform it before value mapping, and returns the transformed value (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8880>`)

- **check_set_errors** (`bool`) – Enables error checks after setting a value (default: `False`)

- **dynamic** (`bool`) – Indicates whether property parameters are intended to be changed on instances or subclasses. See `control()` for a usage example. (default: `False`)

Return type:

`Union`[`property`, `DynamicProperty`]
