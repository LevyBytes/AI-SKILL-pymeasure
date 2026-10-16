# pymeasure.experiment.parameters.Parameter

Class constructor: *pymeasure.experiment.parameters.Parameter* accepts *name*, *default=None*, *ui_class=None*, *group_by=None*, *group_condition=True*, and *description=None*.

Represents an experiment parameter, including the name and units when provided.

Variables:

**value** - Current value of the parameter

Parameters:

- **name** – The parameter name

- **default** - Default value (default: `None`)

- **ui_class** - Qt class used for this parameter's UI (default: `None`)

- **group_by** - Identifies the Parameter(s) controlling whether the associated input is visible. It may be one string for a Parameter name, a dict containing {"Parameter name": condition} pairs, or a list of strings when multiple Parameter names are involved. (default: `None`)

- **group_condition** - Condition checked against the group_by Parameter to control this parameter's visibility; provide it as a value or a (lambda)function. When the group_by argument is a list of strings, this argument may be either one condition or a list of conditions. When the group_by argument is a dict, this argument is ignored. (default: `True`)

Description:

A human-friendly description string for the parameter.

## Related property contracts

- Open when checking pymeasure.experiment.parameters.Parameter.cli_args: [cli_args](cli-args.md).
