# pymeasure.instruments.keithley.Keithley2200.MultiChannelCreator

[Owning PyMeasure class, adapter and connection contract](../keithley2200/overview.md)

*class *MultiChannelCreator(*cls*, *id=None*, *prefix='ch_'*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Register multiple channels on the parent class.

During instantiation, each child is attached to the parent instance with `CommonBase.add_child()`. The attribute name, for example `channels`, becomes the child collection. A custom attribute prefix can be specified. Unless another requirement applies, use `channels` for the attribute name and keep the default prefix `"ch_"`.

```python
from pymeasure.instruments.instrument import Instrument

class Extreme5000(Instrument):
    # Three channels of the same type: 'ch_A', 'ch_B', 'ch_C'
    # and add them to the 'channels' collection
    channels = Instrument.MultiChannelCreator(Extreme5000Channel, ["A", "B", "C"])
    # Two channel interfaces of different types: 'fn_power', 'fn_voltage'
    # and add them to the 'functions' collection
    functions = Instrument.MultiChannelCreator((PowerChannel, VoltageChannel),
                                    ["power", "voltage"], prefix="fn_")

```

Parameters:

- **cls** (`Union`[`type`[`Child`], `Sequence`[`type`[`Child`]]]) – Class applied to every child, or a tuple/list giving a separate class for each child.

- **id** (`Union`[`int`, `str`, `None`]) – tuple/list of instrument channel ids. (default: `None`)

- **prefix** (`Optional`[`str`]) – Attribute prefix for the collection; e.g. “ch_” creates self.ch_A. If prefix evaluates False, the child is attached directly under the variable name. Required when id is tuple/list. (default: `'ch_'`)

- ****kwargs** – Keyword arguments passed to every child.
