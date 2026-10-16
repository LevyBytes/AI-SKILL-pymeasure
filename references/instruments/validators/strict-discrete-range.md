# pymeasure.instruments.validators.strict_discrete_range

pymeasure.instruments.validators.strict_discrete_range(*value*, *values*, *step*)

Creates a validator function that returns the input value only when it is above the range minimum, below the range maximum, and a multiple of step; otherwise it raises a ValueError.

Parameters:

- **value** – A value to test

- **values** - range of values, for example range, list, etc.

- **step** – Minimum stepsize (resolution limit)

Raises:

ValueError when the value falls outside the range
