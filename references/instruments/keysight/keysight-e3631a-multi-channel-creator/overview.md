# pymeasure.instruments.keysight.KeysightE3631A.MultiChannelCreator

[Owning PyMeasure class, adapter and connection contract](../keysight-e3631a/overview.md)

*class *MultiChannelCreator(*cls*, *id=None*, *prefix='ch_'*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Attach multiple channels to the parent class.

At instantiation, `CommonBase.add_child()` attaches the children to the parent instance. The attribute name (e.g. `channels`) becomes the child collection. You can set an attribute prefix; unless another design requires it, name the attribute `channels` and keep the default prefix `"ch_"`.

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

- **cls** (`Union`[`type`[`Child`], `Sequence`[`type`[`Child`]]]) – Child class shared by all children, or a tuple/list containing one class for each child.

- **id** (`Union`[`int`, `str`, `None`]) – Tuple/list of instrument channel ids. (default: `None`)

- **prefix** (`Optional`[`str`]) – Prefix used when creating collection attributes; for example, “ch_” creates attribute self.ch_A. If prefix evaluates False, the child is attached directly under the variable name. Required if id is tuple/list. (default: `'ch_'`)

- ****kwargs** – Keyword arguments supplied to every child.
