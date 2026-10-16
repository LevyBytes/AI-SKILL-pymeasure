# pymeasure.instruments.Channel

*class *pymeasure.instruments.Channel(*parent*, *id*, ***kwargs*)

Superclass used for channel definitions.

This class supports dynamic properties in the same style as `Instrument`, but it needs an `Instrument` instance as its communication parent.

`insert_id()` modifies an outgoing command by adding the channel id. By default, it substitutes the Channel placeholder, default "ch", across command strings such as "CHANnel{ch}:foo".

Parameters:

- **parent** (`CommonBase`) - Instrument instance, specifically an `Instrument`, that owns the channel.

- **id** (`Union`[`int`, `str`, `None`]) - Channel identifier as used during communication.
