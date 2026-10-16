# Adding a channel with ChannelCreator

When an instrument has fewer than 16 channels, place a [`ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.ChannelCreator) on each class attribute that represents a channel interface. The [`ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.ChannelCreator) constructor takes two values: the channel class used for that interface and the instrument's channel id assigned to it.

The example sets up both a channel class and an instrument driver class. `VoltageChannel` is the channel class used to control two channels on `ExtremeVoltage5000`. Inside `ExtremeVoltage5000`, the class attributes `output_A` and `output_B` are declared with [`ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.ChannelCreator), so those attributes become the channel interfaces.

```python
from pymeasure.instruments.instrument import Instrument

class VoltageChannel(Channel):
    """A channel of the voltage source."""

    voltage = Channel.control(
        "SOURce{ch}:VOLT?", "SOURce{ch}:VOLT %g",
        """Control the output voltage of this channel.""",
    )

class ExtremeVoltage5000(Instrument):
    """An instrument with channels."""
    output_A = Instrument.ChannelCreator(VoltageChannel, "A")
    output_B = Instrument.ChannelCreator(VoltageChannel, "B")

```

When the instrument class is instantiated, it creates channel-class instances and stores them on the corresponding class-attribute names. The same channel objects are also gathered into a dictionary whose default name is `channels`. You can reach a channel interface by using that attribute name:

```python
extreme_inst = ExtremeVoltage5000('COM3')
# Set channel A voltage
extreme_inst.output_A.voltage = 50
# Read channel B voltage
chan_b_voltage = extreme_inst.output_B.voltage

```

The `channels` collection also provides access to the same channel interfaces:

```python
# Set channel A voltage
extreme_inst.channels['A'].voltage = 50
# Read channel B voltage
chan_b_voltage = extreme_inst.channels['B'].voltage

```
