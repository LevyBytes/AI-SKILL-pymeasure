# pymeasure.instruments.anritsu.AnritsuMS464xB.datablock_header_format

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *datablock_header_format*: Any*

Set how the arbitrary block header is formed for output data.

Valid values are:

| value | description |
| --- | --- |
| 0 | Send a block header whose length is arbitrary. |
| 1 | Use an 11-character fixed-length block header. |
| 2 | Send no block header. Not IEEE 488.2 compliant. |
