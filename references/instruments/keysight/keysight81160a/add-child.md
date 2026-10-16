# pymeasure.instruments.keysight.Keysight81160A.add_child

[Owning PyMeasure class, adapter and connection contract](overview.md)

add_child(*cls*, *id=None*, *collection='channels'*, *prefix='ch_'*, *attr_name=''*, ***kwargs*)

Create a child on this instance, then return that child's position in the children list.

The created child can be reached through the children dictionary by id or through the generated attribute. Example: a fifth channel with id “F” may be addressed both ways: `instrument.channels["F"] == instrument.ch_F`

Note

Keep the default collection and prefix values unless separate child collections must be identified, for example different channel types (analog and digital).

Parameters:

- **cls** (`type`[`TypeVar`(`child`, bound= `Child`)]) – Channel class to instantiate.

- **id** (`Union`[`int`, `str`, `None`]) – Communication id used for the child, for example “A”. (default: `None`)

- **collection** (`str`) – Child collection name used for dictionary access to channel interfaces. (default: `'channels'`)

- **prefix** (`Optional`[`str`]) – Prefix used when generating several channel interface attributes; for example, “ch_” is put before the channel attribute name self.ch_A. If prefix evaluates False, the child is attached directly under the collection name. (default: `'ch_'`)

- **attr_name** (`Optional`[`str`]) – For a single channel interface, attr_name supplies the attribute name assigned to that channel interface. (default: `''`)

- ****kwargs** – Keyword arguments provided to the channel creator.

Returns:

`TypeVar`(`child`, bound= `Child`) – Created child instance.
