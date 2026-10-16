# pymeasure.instruments.lecroy.LeCroyT3DSO1204.MultiChannelCreator

[Owning PyMeasure class, adapter and connection contract](../le-croy-t3dso1204/overview.md)

*class *MultiChannelCreator(*cls*, *id=None*, *prefix='ch_'*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Attach multiple channels to the parent class.

At instantiation, the children are registered on the parent instance using `CommonBase.add_child()`. The attribute name, for example `channels`, becomes the collection that holds the child objects. A custom attribute prefix may be supplied; absent a specific need, use `channels` for the attribute and keep the default `"ch_"` prefix.

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

- **cls** (`Union`[`type`[`Child`], `Sequence`[`type`[`Child`]]]) – One class for every child, or a tuple/list containing the class for each child.

- **id** (`Union`[`int`, `str`, `None`]) – Tuple/list of instrument channel ids. (default: `None`)

- **prefix** (`Optional`[`str`]) – Prefix used for collection attributes; for example, “ch_” creates self.ch_A. If prefix evaluates False, the child is attached directly under the variable name. Required when id is a tuple/list. (default: `'ch_'`)

- ****kwargs** – Keyword arguments supplied to every child.
