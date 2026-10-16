# pymeasure.instruments.common_base.CommonBase.setting

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *setting(*set_command*, *docs*, *validator=<function CommonBase.&lt;lambda&gt;>*, *values=()*, *map_values=False*, *set_process=<function CommonBase.&lt;lambda&gt;>*, *check_set_errors=False*, *dynamic=False*)

Create a class property from the provided commands. The resulting property is write-only and raises an exception if read from the instrument.

Parameters:

- **set_command** (`str`) - String command that writes the value.

- **docs** (`str`) - Docstring text added to the generated documentation.

- **validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `Any`]) - Function that receives a value plus the valid-values group and returns an accepted value, or raises an exception otherwise. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f87d0>`)

- **values** (`TypeVar`(`Vs`)) - Valid-value collection, such as a list, tuple, range, or dictionary; it can also provide mappings when `map_values` is True. (default: `()`)

- **map_values** (`bool`) - Boolean switch indicating whether values should be handled as a mapping. (default: `False`)

- **set_process** (`Callable`[[`Any`], `Any`]) - Function that receives a value, processes it before value mapping, and returns the processed result. (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8880>`)

- **check_set_errors** (`bool`) - Enables or disables error checks after setting. (default: `False`)

- **dynamic** (`bool`) - Controls whether property parameters are intended to vary on instances or subclasses. See `control()` for an usage example. (default: `False`)

Return type:

`Union`[`property`, `DynamicProperty`]
