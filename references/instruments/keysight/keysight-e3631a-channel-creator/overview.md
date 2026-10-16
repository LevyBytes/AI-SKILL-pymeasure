# pymeasure.instruments.keysight.KeysightE3631A.ChannelCreator

[Owning PyMeasure class, adapter and connection contract](../keysight-e3631a/overview.md)

*class *ChannelCreator(*cls*, *id=None*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Attach one channel to the parent class.

At instantiation, `CommonBase.add_child()` attaches the child to the parent instance. The Instrument class attribute that received ChannelCreator becomes the channel interface name.

```python
from pymeasure.instruments.instrument import Instrument

class Extreme5000(Instrument):
    # Two output channels, accessible by their property names
    # and both are accessible through the 'channels' collection
    output_A = Instrument.ChannelCreator(Extreme5000Channel, "A")
    output_B = Instrument.ChannelCreator(Extreme5000Channel, "B")
    # A channel without a channel accessible through the 'motor' collection
    motor = Instrument.ChannelCreator(MotorControl)

inst = SomeInstrument()
# Set the extreme_temp for channel A of Extreme5000 instrument
inst.output_A.extreme_temp = 42

```

Parameters:

- **cls** (`type`[`Child`]) – Channel class used for the channel interface

- **id** (`Union`[`int`, `str`, `None`]) – Instrument channel id as an integer or string. (default: `None`)

- ****kwargs** – Keyword arguments supplied to every child.
