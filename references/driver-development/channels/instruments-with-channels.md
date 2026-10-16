# Instruments with channels

Oscilloscopes, voltage sources, and similar instruments often expose channels where the command text changes only by channel name. PyMeasure handles that pattern with [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel), a companion to [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument) and its property factories. Unlike those factories, it is constructed with a parent [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument) instance rather than an [`Adapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.Adapter) argument. The channel sends all I/O through the parent instrument's methods, such as `write`, `read`, and related calls. [`Channel.insert_id`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel.insert_id) calls `str.format` so the channel id replaces every occurrence of the `Channel.placeholder` class attribute in commands being written; the default placeholder is `"ch"`. Thus, when the channel id is `"3"`, `"Ch{ch}:VOLT?"` is emitted to the device as `"Ch3:VOLT?"`.

Document each channel class that gets created. In the documentation file for the instrument, include:

```rst
.. autoclass:: pymeasure.instruments.MANUFACTURER.INSTRUMENT.CHANNEL
    :members:
    :show-inheritance:

```

MANUFACTURER names the manufacturer folder. INSTRUMENT names the instrument-definition file, and that file contains the CHANNEL class. From the instrument's docstring, the channel can be referenced with `:class:`CHANNEL``.

Two helper classes standardize how an `Instrument` class defines channels. Use [`ChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.ChannelCreator) for instruments with fewer than 16 channels, where every channel is declared explicitly. Use [`MultiChannelCreator`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.MultiChannelCreator) for instruments with more than 16 channels, because it can define many channels with one declaration.
