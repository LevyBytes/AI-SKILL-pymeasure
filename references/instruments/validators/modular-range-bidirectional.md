# pymeasure.instruments.validators.modular_range_bidirectional

pymeasure.instruments.validators.modular_range_bidirectional(*value*, *values*)

Creates a validator function that yields the input value when it belongs to the range; otherwise, it yields that value modulo the range maximum. Negative values are allowed.

Parameters:

- **value** – a value to test

- **values** - valid values as a set
