# Channels

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Instruments with channels

Oscilloscopes, voltage sources, and similar instruments often expose channels where the command text changes only by channel name. PyMeasure handles that pattern with [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel), a companion to [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument) and its property factories. Unlike those factories, it is constructed with a parent [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument) instance rather than an [`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter) argument. The channel sends all I/O through the parent instrument's methods, such as `write`, `read`, and related calls. [`Channel.insert_id`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel.insert_id) calls `str.format` so the channel id replaces every occurrence of the `Channel.placeholder` class attribute in commands being written; the default placeholder is `"ch"`. Thus, when the channel id is `"3"`, `"Ch{ch}:VOLT?"` is emitted to the device as `"Ch3:VOLT?"`.

Document each channel class that gets created. In the documentation file for the instrument, include:

```python
.. autoclass:: pymeasure.instruments.MANUFACTURER.INSTRUMENT.CHANNEL
    :members:
    :show-inheritance:

```

MANUFACTURER names the manufacturer folder. INSTRUMENT names the instrument-definition file, and that file contains the CHANNEL class. From the instrument's docstring, the channel can be referenced with `:class:`CHANNEL``.

Two helper classes standardize how an `Instrument` class defines channels. Use [`ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.ChannelCreator) for instruments with fewer than 16 channels, where every channel is declared explicitly. Use [`MultiChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.MultiChannelCreator) for instruments with more than 16 channels, because it can define many channels with one declaration.

### Adding a channel with [`ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.ChannelCreator)

When an instrument has fewer than 16 channels, place a [`ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.ChannelCreator) on each class attribute that represents a channel interface. The [`ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.ChannelCreator) constructor takes two values: the channel class used for that interface and the instrument's channel id assigned to it.

The example sets up both a channel class and an instrument driver class. `VoltageChannel` is the channel class used to control two channels on `ExtremeVoltage5000`. Inside `ExtremeVoltage5000`, the class attributes `output_A` and `output_B` are declared with [`ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.ChannelCreator), so those attributes become the channel interfaces.

```python
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

### Adding multiple channels with [`MultiChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.MultiChannelCreator)

For instruments with more than 16 channels, [`MultiChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.MultiChannelCreator) can build a list of channels from one class attribute declaration.

The [`MultiChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.MultiChannelCreator) constructor takes either one channel class or a list of channel classes, plus the matching channel ids. Tuples may be supplied in place of lists. Passing one class together with a list of ids makes every generated channel use that same class.

At instrument instantiation, channel interfaces are created with attribute names built from the prefix, default `"ch_"`, followed by the channel id; for example, id `"A"` becomes `ch_A`. [`ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.ChannelCreator) maps each class attribute to one channel interface, whereas [`MultiChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.MultiChannelCreator) puts a channel collection on the class attribute where it is assigned. Use `channels` as that class attribute name to keep the codebase homogenous.

For the revised example, [`MultiChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.MultiChannelCreator) is used to produce 24 `VoltageChannel` channels.

```python
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

### Advanced channel management

### Adding / removing channels

When channels need to be added or removed programmatically, call the parent object's [`add_child()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.add_child), [`remove_child()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.remove_child) methods.

### Channels with fixed prefix

Override a channel's `insert_id()` method when every command for that channel must carry a fixed prefix, such as `"SOURceA:"` for channel A. This is especially useful when only one channel uses that type, for example because it represents one instrument function rather than another.

```python
class VoltageChannelPrefix(Channel):
    """A channel of a voltage source, every command has the same prefix."""

    def insert_id(self, command):
        return f"SOURce{self.id}:{command}"

    voltage = Channel.control(
        "VOLT?", "VOLT %g",
        """Control the output voltage of this channel.""",
    )

```

This channel class performs the same communication as the earlier example, but the channel prefix is handled inside `insert_id()` instead of being repeated in each property created by `control()`.

### Collections of different channel types

Devices may expose multiple channel types. For that arrangement, set separate `collection` and `prefix` parameters.

```python
class PowerChannel(Channel):
    """A channel controlling the power."""
    power = Channel.measurement(
        "POWER?", """Measure the currently consumed power.""")

class MultiChannelTypeInstrument(Instrument):
    """An instrument with two different channel types."""
    analog = Instrument.MultiChannelCreator(
        (VoltageChannel, VoltageChannelPrefix),
        ("A", "B"),
        prefix="an_")
    digital = Instrument.MultiChannelCreator(VoltageChannel, (0, 1, 2), prefix="di_")
    power = Instrument.ChannelCreator(PowerChannel)

```

The instrument defines two channel collections plus a standalone channel. In the `analog` dictionary, the first collection has a `VoltageChannel` instance named `an_A` and a `VoltageChannelPrefix` instance named `an_B`. The second collection is stored in `digital`; it contains three `VoltageChannel` channels named `di_0, di_1, di_2`. The first channel in that second group is reachable as either `inst.di_0` or `inst.digital[0]`. The standalone channel is named `power`, and it has no prefix.

When there is only one channel category, leave the default parameters of [`ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.ChannelCreator) or [`add_child()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.add_child) unchanged so the code base remains homogeneous. The default behaviour is expected to cover most use cases.
