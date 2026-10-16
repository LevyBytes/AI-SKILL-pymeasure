# pymeasure.instruments.keithley.Keithley2200.ChannelCreator

[Owning PyMeasure class, adapter and connection contract](../keithley2200/overview.md)

*class *ChannelCreator(*cls*, *id=None*, ***kwargs*)

Bases: [`BaseChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.BaseChannelCreator)

Register one channel on the parent class.

At instantiation, the child is attached to the parent instance through `CommonBase.add_child()`. The channel interface uses the Instrument class attribute name that held the ChannelCreator assignment.

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

- **cls** (`type`[`Child`]) – Channel class used for the channel interface.

- **id** (`Union`[`int`, `str`, `None`]) – Channel id on the instrument, as an integer or string. (default: `None`)

- ****kwargs** – Keyword arguments passed to every child.
