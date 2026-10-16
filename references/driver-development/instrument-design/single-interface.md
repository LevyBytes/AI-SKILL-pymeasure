# Single interface

The simplest form, useful when default settings are needed, forwards all keyword arguments to the `Instrument` initializer, which passes them through to [`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter) when `adapter` is a string or integer.

```python
def __init__(self, adapter, name="Extreme 5000", **kwargs):
    super().__init__(
        adapter,
        name,
        **kwargs
    )

```

Put defaults in the signature when they should be obvious to users and may be overridden. This fits instruments with a single interface type, or defaults that are valid across every interface type; see [`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter) documentation for details.

```python
def __init__(self, adapter, name="Extreme 5000", baud_rate=2400, **kwargs):
    super().__init__(
        adapter,
        name,
        baud_rate=baud_rate,
        **kwargs
    )

```

When defaults are needed but do not need prominent exposure for replacement, use this pattern; it sets the value only if `kwargs` does not already contain an entry.

```python
def __init__(self, adapter, name="Extreme 5000", **kwargs):
    kwargs.setdefault('timeout', 1500)
    super().__init__(
        adapter,
        name,
        **kwargs
    )

```
