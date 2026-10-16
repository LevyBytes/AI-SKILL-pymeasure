# pymeasure.instruments.validators.truncated_discrete_set

pymeasure.instruments.validators.truncated_discrete_set(*value*, *values*)

Creates a validator function that gives back the value when it is in the discrete set; if not, it gives back the smallest set value greater than the value.

Parameters:

- **value** – A value to test

- **values** - valid values as a set
