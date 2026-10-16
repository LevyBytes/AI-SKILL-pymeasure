# pymeasure.instruments.lecroy.LeCroyT3DSO1204.add_child

[Owning PyMeasure class, adapter and connection contract](overview.md)

add_child(*cls*, *id=None*, *collection='channels'*, *prefix='ch_'*, *attr_name=''*, ***kwargs*)

Attach a child to this instance and return its position in the children list.

The created child can be reached through its id in the children dictionary or through the generated attribute. For example, an instrument fifth channel with id “F” can be accessed either way: `instrument.channels["F"] == instrument.ch_F`

Note

Keep the default collection and prefix values unless separate child collections must be distinguished, such as analog and digital channel types.

Parameters:

- **cls** (`type`[`TypeVar`(`child`, bound= `Child`)]) – Channel class.

- **id** (`Union`[`int`, `str`, `None`]) – Child id used for communication, such as “A”. (default: `None`)

- **collection** (`str`) – Name of the child collection used for dictionary access to channel interfaces. (default: `'channels'`)

- **prefix** (`Optional`[`str`]) – Prefix added when creating multiple channel interface attributes; for example, “ch_” produces self.ch_A. If prefix evaluates False, the child is attached directly below the collection name. (default: `'ch_'`)

- **attr_name** (`Optional`[`str`]) – For a single channel interface, attr_name supplies the attribute name used when the interface is assigned. (default: `''`)

- ****kwargs** – Keyword arguments forwarded to the channel creator.

Returns:

`TypeVar`(`child`, bound= `Child`) – Newly created child instance.
