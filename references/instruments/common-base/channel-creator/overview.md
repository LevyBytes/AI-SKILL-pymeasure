# pymeasure.instruments.common_base.CommonBase.ChannelCreator

[Owning PyMeasure class, adapter and connection contract](../overview.md)

*class *ChannelCreator(*cls*, *id=None*, ***kwargs*)

Attach one channel to the parent class.

During instantiation, the child is attached to the parent instance through `CommonBase.add_child()`. The channel interface takes its name from the attribute assigned to ChannelCreator on the Instrument class.

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

- **cls** (`type`[`Child`]) - Channel class used for the channel interface.

- **id** (`Union`[`int`, `str`, `None`]) - Instrument-side channel id, supplied as an integer or string. (default: `None`)

- ****kwargs** - Keyword arguments applied to every child.
