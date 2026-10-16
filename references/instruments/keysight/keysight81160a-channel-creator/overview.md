# pymeasure.instruments.keysight.Keysight81160A.ChannelCreator

[Owning PyMeasure class, adapter and connection contract](../keysight81160a/overview.md)

*class *ChannelCreator(*cls*, *id=None*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Attach one channel to the parent class.

When the parent instance is created, `CommonBase.add_child()` attaches the child. The attribute that holds the ChannelCreator inside the Instrument class becomes the channel interface name.

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

- **id** (`Union`[`int`, `str`, `None`]) – Instrument-side channel id, supplied as an integer or string. (default: `None`)

- ****kwargs** – Keyword arguments passed through to every child.
