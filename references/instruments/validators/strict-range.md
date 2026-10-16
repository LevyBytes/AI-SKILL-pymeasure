# pymeasure.instruments.validators.strict_range

pymeasure.instruments.validators.strict_range(*value*, *values*)

Creates a validator function that accepts the value only when it falls between the minimum and maximum entries in `values`, inclusive; otherwise it raises a ValueError.

Parameters:

- **value** – A value to test

- **values** - range of values, for example range, list, etc.

Raises:

ValueError when the value falls outside the range
