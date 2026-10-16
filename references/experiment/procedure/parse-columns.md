# pymeasure.experiment.procedure.Procedure.parse_columns

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *parse_columns(*columns*)

Parses columns that include units in parentheses. For each column, when matching parentheses hold text with no spaces, the enclosed value is treated as a Pint unit. Example: "Source Voltage (V)" is parsed and matched to `Unit('volt')`. Raises an error if the parsed value is not defined in the Pint unit registry. Returns a dictionary mapping matched columns to their units.

Parameters:

**columns** - List of columns to parse.

Returns:

Dictionary of columns with Pint units.
