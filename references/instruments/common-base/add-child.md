# pymeasure.instruments.common_base.CommonBase.add_child

[Owning PyMeasure class, adapter and connection contract](overview.md)

add_child(*cls*, *id=None*, *collection='channels'*, *prefix='ch_'*, *attr_name=''*, ***kwargs*)

Create a child on this instance and return its position in the children list.

After creation, the child can be reached through its id in the children dictionary or through the generated attribute; for example, the fifth channel with id "F" can be accessed as `instrument.channels["F"] == instrument.ch_F`.

Note

Keep the default collection and prefix unless separate child collections must be distinguished, such as analog and digital channel types.

Parameters:

- **cls** (`type`[`TypeVar`(`child`, bound= `Child`)]) - Class used for the channel.

- **id** (`Union`[`int`, `str`, `None`]) - Communication id for the child, such as "A". (default: `None`)

- **collection** (`str`) - Child collection name used for dictionary-style access to channel interfaces. (default: `'channels'`)

- **prefix** (`Optional`[`str`]) - Prefix placed before the channel interface attribute name when creating several channel interfaces, such as "ch_" in self.ch_A. If prefix evaluates False, the child is attached directly below the collection name. (default: `'ch_'`)

- **attr_name** (`Optional`[`str`]) - For a single channel interface, attr_name supplies the attribute name used for that interface. (default: `''`)

- ****kwargs** - Keyword arguments passed to the channel creator.

Returns:

`TypeVar`(`child`, bound= `Child`) - Newly created child instance.
