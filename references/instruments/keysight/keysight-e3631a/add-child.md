# pymeasure.instruments.keysight.KeysightE3631A.add_child

[Owning PyMeasure class, adapter and connection contract](overview.md)

add_child(*cls*, *id=None*, *collection='channels'*, *prefix='ch_'*, *attr_name=''*, ***kwargs*)

Create a child on this instance, then return its position in the children list.

The created child can be reached through its id in the children dictionary or through the generated attribute; for example, the fifth channel of instrument with id “F” can be checked with `instrument.channels["F"] == instrument.ch_F`

Note

Keep the default collection and prefix parameter unless separate child collections must be distinguished, such as analog and digital channel types.

Parameters:

- **cls** (`type`[`TypeVar`(`child`, bound= `Child`)]) – Channel class.

- **id** (`Union`[`int`, `str`, `None`]) – Child id used during communication, e.g. “A”. (default: `None`)

- **collection** (`str`) – Child collection name used for dictionary access to channel interfaces. (default: `'channels'`)

- **prefix** (`Optional`[`str`]) – Prefix for multiple channel interfaces; for example, “ch_” is placed before the channel interface attribute name self.ch_A. If prefix evaluates False, the child is attached directly under the collection name. (default: `'ch_'`)

- **attr_name** (`Optional`[`str`]) – When creating one channel interface, attr_name supplies the attribute name assigned to that channel interface. (default: `''`)

- ****kwargs** – Keyword arguments passed to the channel creator.

Returns:

`TypeVar`(`child`, bound= `Child`) – Created child instance.
