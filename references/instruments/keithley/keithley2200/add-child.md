# pymeasure.instruments.keithley.Keithley2200.add_child

[Owning PyMeasure class, adapter and connection contract](overview.md)

add_child(*cls*, *id=None*, *collection='channels'*, *prefix='ch_'*, *attr_name=''*, ***kwargs*)

Attach a child to this instance, then return its position in the children list.

The created child can be reached through the children dictionary by id or through its generated attribute; for example, the fifth channel of instrument with id “F” is available as `instrument.channels["F"] == instrument.ch_F`.

Note

Keep the default collection and prefix settings unless multiple child collections must be separated, such as analog and digital channel types.

Parameters:

- **cls** (`type`[`TypeVar`(`child`, bound= `Child`)]) – Channel class to instantiate.

- **id** (`Union`[`int`, `str`, `None`]) – Child id used during communication, e.g. “A”. (default: `None`)

- **collection** (`str`) – Child-collection name used for dictionary lookup of channel interfaces. (default: `'channels'`)

- **prefix** (`Optional`[`str`]) – Prefix used when building several channel interfaces; e.g. “ch_” is prepended to produce self.ch_A. If prefix evaluates False, the child is attached directly under the collection name. (default: `'ch_'`)

- **attr_name** (`Optional`[`str`]) – For a single channel interface, attr_name supplies the attribute name assigned to that interface. (default: `''`)

- ****kwargs** – Keyword arguments supplied to the channel creator.

Returns:

`TypeVar`(`child`, bound= `Child`) – Created child instance.
