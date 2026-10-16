# Adding multiple channels with MultiChannelCreator

For instruments with more than 16 channels, [`MultiChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.MultiChannelCreator) can build a list of channels from one class attribute declaration.

The [`MultiChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.MultiChannelCreator) constructor takes either one channel class or a list of channel classes, plus the matching channel ids. Tuples may be supplied in place of lists. Passing one class together with a list of ids makes every generated channel use that same class.

At instrument instantiation, channel interfaces are created with attribute names built from the prefix, default `"ch_"`, followed by the channel id; for example, id `"A"` becomes `ch_A`. [`ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.ChannelCreator) maps each class attribute to one channel interface, whereas [`MultiChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.MultiChannelCreator) puts a channel collection on the class attribute where it is assigned. Use `channels` as that class attribute name to keep the codebase homogenous.

For the revised example, [`MultiChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.MultiChannelCreator) is used to produce 24 `VoltageChannel` channels.

```python
from pymeasure.instruments.instrument import Instrument

class VoltageChannel(Channel):
    """A channel of the voltage source."""

    voltage = Channel.control(
        "SOURce{ch}:VOLT?", "SOURce{ch}:VOLT %g",
        """Control the output voltage of this channel.""",
    )

class MultiExtremeVoltage5000(Instrument):
    """An instrument with channels."""
    channels = Instrument.MultiChannelCreator(VoltageChannel, list(range(1,25)))

```

The generated class attributes can now be used to access channel interfaces:

```python
extreme_inst = MultiExtremeVoltage5000('COM3')
# Set channel 5 voltage
extreme_inst.ch_5.voltage = 50
# Read channel 16 voltage
chan_16_voltage = extreme_inst.ch_16.voltage

```

Since the class attribute assigned to `MultiChannelCreator` is `channels`, the channel interfaces are also available through the `channels` collection:

```python
# Set channel 10 voltage
extreme_inst.channels[10].voltage = 50
# Read channel 22 voltage
chan_b_voltage = extreme_inst.channels[22].voltage

```
