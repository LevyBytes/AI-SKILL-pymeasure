# pymeasure.instruments.keysight.Keysight81160A.MultiChannelCreator

[Owning PyMeasure class, adapter and connection contract](../keysight81160a/overview.md)

*class *MultiChannelCreator(*cls*, *id=None*, *prefix='ch_'*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Attach multiple channels to the parent class.

During parent instantiation, `CommonBase.add_child()` creates each child. The assigned attribute name, such as `channels`, becomes the child collection. A custom attribute prefix can be supplied. In normal cases, choose `channels` for the attribute and keep the default prefix `"ch_"`.

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

- **cls** (`Union`[`type`[`Child`], `Sequence`[`type`[`Child`]]]) – One class used for every child, or a tuple/list giving a separate class for each child.

- **id** (`Union`[`int`, `str`, `None`]) – tuple/list containing the instrument channel ids. (default: `None`)

- **prefix** (`Optional`[`str`]) – Attribute collection prefix; for example, “ch_” produces self.ch_A. If prefix evaluates False, the child is placed directly below the variable name. Required if id is tuple/list. (default: `'ch_'`)

- ****kwargs** – Keyword arguments passed through to every child.
