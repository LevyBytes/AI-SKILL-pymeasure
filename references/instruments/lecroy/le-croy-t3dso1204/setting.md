# pymeasure.instruments.lecroy.LeCroyT3DSO1204.setting

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *setting(*set_command*, *docs*, *validator=<function CommonBase.&lt;lambda&gt;>*, *values=()*, *map_values=False*, *set_process=<function CommonBase.&lt;lambda&gt;>*, *check_set_errors=False*, *dynamic=False*)

Create a class property from the supplied commands. This set-only property can be written, and reading it from the instrument raises an exception.

Parameters:

- **set_command** (`str`) – String command used to write the value.

- **docs** (`str`) – Docstring text inserted into the documentation.

-
**validator** (`Callable`[[`Any`, `TypeVar`(`Vs`)], `Any`]) - Callable that receives the candidate value together with the valid-value group; it returns an accepted value or raises an exception (default: `<function CommonBase.<lambda> at 0x7aa5aa7f87d0>`)

- **values** (`TypeVar`(`Vs`)) - Valid choices supplied as a list, tuple, range, or dictionary; when `map_values` is True, the entries may also map inputs to outputs. (default: `()`)

- **map_values** (`bool`) - Boolean switch indicating whether `values` should be treated as a mapping (default: `False`)

- **set_process** (`Callable`[[`Any`], `Any`]) - Callable applied to the incoming value before value mapping; it returns the processed value (default: `<function CommonBase.<lambda> at 0x7aa5aa7f8880>`)

- **check_set_errors** (`bool`) - Enables or disables error checking after a set operation (default: `False`)

- **dynamic** (`bool`) - Indicates whether instances or subclasses are expected to alter the property parameters. For a usage example, see `control()`. (default: `False`)

Return type:

`Union`[`property`, `DynamicProperty`]
