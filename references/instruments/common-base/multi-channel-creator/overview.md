# pymeasure.instruments.common_base.CommonBase.MultiChannelCreator

[Owning PyMeasure class, adapter and connection contract](../overview.md)

*class *MultiChannelCreator(*cls*, *id=None*, *prefix='ch_'*, ***kwargs*)

Attach multiple channels to the parent class.

At instantiation time, the children are attached to the parent instance with `CommonBase.add_child()`. The attribute name, for example `channels`, becomes the child collection. A custom attribute prefix can be supplied. Unless there is a specific reason to choose differently, use `channels` for the attribute name and keep the default prefix `"ch_"`.

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

- **cls** (`Union`[`type`[`Child`], `Sequence`[`type`[`Child`]]]) - Class shared by all children, or a tuple/list containing one class for each child.

- **id** (`Union`[`int`, `str`, `None`]) - tuple/list containing the instrument channel ids. (default: `None`)

- **prefix** (`Optional`[`str`]) - Attribute collection prefix; for example, "ch_" creates self.ch_A. If prefix evaluates False, the child is placed directly under the variable name. Required when id is a tuple/list. (default: `'ch_'`)

- ****kwargs** - Keyword arguments applied to every child.
