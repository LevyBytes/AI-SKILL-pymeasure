# pymeasure.instruments.keysight.KeysightE36312A.add_child

[Owning PyMeasure class, adapter and connection contract](overview.md)

add_child(*cls*, *id=None*, *collection='channels'*, *prefix='ch_'*, *attr_name=''*, ***kwargs*)

Attach a child to this instance, then return its position in the children list.

The created child can be reached through the children dictionary by id or through the generated attribute; for example, the fifth channel of an instrument with id “F” can be accessed either way: `instrument.channels["F"] == instrument.ch_F`

Note

Leave the default collection and prefix parameter unchanged unless separate collections of different children must be distinguished, such as analog and digital channel types.

Parameters:

- **cls** (`type`[`TypeVar`(`child`, bound= `Child`)]): Channel class to instantiate.

- **id** (`Union`[`int`, `str`, `None`]): Child id as used during communication, for example “A”. (default: `None`)

- **collection** (`str`): Collection name for dictionary access to the channel interfaces. (default: `'channels'`)

- **prefix** (`Optional`[`str`]): When multiple channel interfaces are created, the prefix such as “ch_” is added before the channel interface attribute name self.ch_A. If prefix evaluates False, the child is attached directly beneath the collection name. (default: `'ch_'`)

- **attr_name** (`Optional`[`str`]): For a single channel interface, attr_name supplies the attribute name assigned to that channel interface. (default: `''`)

- ****kwargs** — Keyword arguments passed to the channel creator.

Returns:

`TypeVar`(`child`, bound= `Child`): Created child instance.
