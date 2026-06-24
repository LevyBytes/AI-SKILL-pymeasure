# Validators

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Validator functions

Validators work with `Instrument.control` or `Instrument.setting` to support properties whose allowed values need more than simple constraints. The [Restricting values with validators](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#validators) section gives the fuller explanation.

 pymeasure.instruments.validators.discreteTruncate(*number*, *discreteSet*)

Cuts the number back to the nearest member of the positive discrete set. It returns False when the number is negative or exceeds the maximum value.

 pymeasure.instruments.validators.joined_validators(**validators*)

Builds and returns a validator function that combines a list of validators.

When the supplied value satisfies at least one validator rather than all validators, the validator returns that value; if none accept it, it raises a ValueError.

Note: the combined validator expects `values` to be a sequence whose entries match the `values` required by the corresponding validators; those entries are often sequences too.

Example:

```python
>>> from pymeasure.instruments.validators import strict_discrete_set, strict_range
>>> from pymeasure.instruments.validators import joined_validators
>>> joined_v = joined_validators(strict_discrete_set, strict_range)
>>> values = [['MAX','MIN'], range(10)]
>>> joined_v(5, values)
5
>>> joined_v('MAX', values)
'MAX'
>>> joined_v('NONSENSE', values)
Traceback (most recent call last):
...
ValueError: Value of NONSENSE does not match any of the joined validators

```

Parameters:

**validators** - iterable of other validators

 pymeasure.instruments.validators.modular_range(*value*, *values*)

Creates a validator function that yields the input value when it belongs to the range; otherwise, it yields that value modulo the range maximum.

Parameters:

-

**value** – a value to test

-

**values** - valid values as a set

 pymeasure.instruments.validators.modular_range_bidirectional(*value*, *values*)

Creates a validator function that yields the input value when it belongs to the range; otherwise, it yields that value modulo the range maximum. Negative values are allowed.

Parameters:

-

**value** – a value to test

-

**values** - valid values as a set

 pymeasure.instruments.validators.strict_discrete_range(*value*, *values*, *step*)

Creates a validator function that returns the input value only when it is above the range minimum, below the range maximum, and a multiple of step; otherwise it raises a ValueError.

Parameters:

-

**value** – A value to test

-

**values** - range of values, for example range, list, etc.

-

**step** – Minimum stepsize (resolution limit)

Raises:

ValueError when the value falls outside the range

 pymeasure.instruments.validators.strict_discrete_set(*value*, *values*)

Creates a validator function that gives back the value when it appears in the discrete set; otherwise it raises a ValueError.

Parameters:

-

**value** – A value to test

-

**values** - valid values as a set

Raises:

ValueError when the value is absent from the set

 pymeasure.instruments.validators.strict_range(*value*, *values*)

Creates a validator function that accepts the value only when it falls between the minimum and maximum entries in `values`, inclusive; otherwise it raises a ValueError.

Parameters:

-

**value** – A value to test

-

**values** - range of values, for example range, list, etc.

Raises:

ValueError when the value falls outside the range

 pymeasure.instruments.validators.truncated_discrete_set(*value*, *values*)

Creates a validator function that gives back the value when it is in the discrete set; if not, it gives back the smallest set value greater than the value.

Parameters:

-

**value** – A value to test

-

**values** - valid values as a set

 pymeasure.instruments.validators.truncated_range(*value*, *values*)

Creates a validator function that gives back the value when it lies in the range; otherwise it gives back the nearest bound of that range.

Parameters:

-

**value** – A value to test

-

**values** - valid values as a set
