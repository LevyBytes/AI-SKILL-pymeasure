# Multiple interfaces

With instruments that have multiple interfaces (e.g. serial, TCPI/IP, USB), the setup becomes more complex. Some settings may apply to every interface, such as `timeout`, while others are valid for only one interface type.

The useful pattern is to add keyword arguments named for interface types, such as `asrl` or `gpib` below; the full list is [here](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType). Each keyword then holds a *dictionary* of settings for that specific interface:

```python
def __init__(self, adapter, name="Extreme 5000", baud_rate=2400, **kwargs):
    kwargs.setdefault('timeout', 1500)
    super().__init__(
        adapter,
        name,
        gpib=dict(enable_repeat_addressing=False,
                  read_termination='\r'),
        asrl={'baud_rate': baud_rate,
              'read_termination': '\r\n'},
        **kwargs
    )

```

On instrument creation, settings for the interface actually in use are merged with `**kwargs` before being sent to PyVISA; settings for other interfaces are discarded. This keeps the forwarded argument set valid. Entries already present in `**kwargs**` take precedence, so users can *still* override any defaults from the instrument definition when necessary.

For many instruments, the first simple approach is sufficient. When the connection arrangement is more complex, check whether [Advanced communication protocols](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/advanced_communication.html#advanced-communication-protocols) covers it. If an unusual connection type cannot be represented with PyVISA, you can implement your own Adapter.
