# pymeasure.experiment.results.replace_placeholders

[Owning PyMeasure class, adapter and connection contract](overview.md)

pymeasure.experiment.results.replace_placeholders(*string*, *procedure*, *date_format='%Y_%m_%d'*, *time_format='%H_%M_%S'*)

Substitutes values from procedure parameters into placeholders in a string.

Replaces placeholders in the supplied string with values from the associated parameters, taken from the procedure. The standard python string.format syntax is used. Besides procedure parameters, referenced by their full names, the optional placeholders "date" and "time" are also available.

Parameters:

- **string** - String whose placeholders should be substituted. Python string.format syntax applies; for example, "{Parameter Name}" inserts a FloatParameter named "Parameter Name", and "{Parameter Name:.2f}" also applies explicit formatting to the parameter.

- **procedure** - Procedure used as the source of parameter values.

- **date_format** - String describing the format for the extra placeholder "date". (default: `'%Y_%m_%d'`)

- **time_format** - String describing the format for the extra placeholder "time". (default: `'%H_%M_%S'`)
