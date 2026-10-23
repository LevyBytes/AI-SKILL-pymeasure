# pymeasure.instruments.agilent.agilent33500.Agilent33500Channel.data_arb

[Owning PyMeasure class, adapter and connection contract](overview.md)

data_arb(*arb_name*, *data_points*, *data_format='DAC'*)

Send an arbitrary trace to a channel's volatile device memory.

data_points accepts one of three encodings: comma separated 16 bit DAC values (from -32767 to +32767), comma separated floating point values (from -1.0 to +1.0), or a binary data stream. For details, consult the manual. Capacity is device-specific and spans 8 Sa to 16 MSa (maximum).

Parameters:

- **arb_name**: Trace name used inside volatile memory; later calls use this name to select that trace.

- **data_points** –

Trace samples supplied individually. Their required representation follows the format parameter.

format = ?DAC? (default): Takes a list of integer values from -32767 to +32767. Requires at least 8 and at most 65536 points.

format = ?float?: Takes a list of floating point values from -1.0 to +1.0. Requires at least 8 and at most 65536 points.

format = ?binary?: Takes an 8 bit binary stream.

- **data_format**: Specifies the representation used for data_points: ?DAC? (default), ?float?, or ?binary?. See the data_points parameter notes above. (default: `'DAC'`)
