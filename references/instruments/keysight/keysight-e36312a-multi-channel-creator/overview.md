# pymeasure.instruments.keysight.KeysightE36312A.MultiChannelCreator

[Owning PyMeasure class, adapter and connection contract](../keysight-e36312a/overview.md)

*class *MultiChannelCreator(*cls*, *id=None*, *prefix='ch_'*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Create multiple channels on the parent class.

At instantiation, the children are attached to the parent instance through `CommonBase.add_child()`. The attribute name, such as `channels`, becomes the child collection. You can choose the attribute prefix. When no stronger reason applies, keep `channels` for the attribute name and use the default `"ch_"` prefix.

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

- **cls** (`Union`[`type`[`Child`], `Sequence`[`type`[`Child`]]]) — Class shared by all children, or a tuple/list with one class per child.

- **id** (`Union`[`int`, `str`, `None`]) — tuple/list containing the instrument channel ids. (default: `None`)

- **prefix** (`Optional`[`str`]) — Collection prefix for attributes; for example, “ch_” creates self.ch_A. If prefix evaluates False, the child is placed directly under the variable name. Required when id is a tuple/list. (default: `'ch_'`)

- ****kwargs** — Keyword arguments supplied to every child.
