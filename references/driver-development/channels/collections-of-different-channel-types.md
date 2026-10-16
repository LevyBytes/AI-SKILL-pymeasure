# Collections of different channel types

Devices may expose multiple channel types. For that arrangement, set separate `collection` and `prefix` parameters.

```python
from pymeasure.instruments.instrument import Instrument

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
