# pymeasure.instruments.validators.joined_validators

pymeasure.instruments.validators.joined_validators(**validators*)

Builds and returns a validator function that combines a list of validators.

When the supplied value satisfies at least one validator rather than all validators, the validator returns that value; if none accept it, it raises a ValueError.

Note: the combined validator expects `values` to be a sequence whose entries match the `values` required by the corresponding validators; those entries are often sequences too.

Example:

```pycon
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
