# pymeasure.instruments.validators.strict_discrete_set

pymeasure.instruments.validators.strict_discrete_set(*value*, *values*)

Creates a validator function that gives back the value when it appears in the discrete set; otherwise it raises a ValueError.

Parameters:

- **value** – A value to test

- **values** - valid values as a set

Raises:

ValueError when the value is absent from the set
