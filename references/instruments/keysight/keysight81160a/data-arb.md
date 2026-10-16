# pymeasure.instruments.keysight.Keysight81160A.data_arb

[Owning PyMeasure class, adapter and connection contract](overview.md)

data_arb(*arb_name*, *data_points*, *data_format='DAC'*)

Upload an arbitrary trace into the device volatile memory.

data_points may be supplied as comma separated 16 bit DAC values, comma separated floating point values, or a binary data stream. DAC entries range from -32767 to +32767. Floating point entries range from -1.0 to +1.0. See the manual for details. Storage is device-type dependent and ranges from 8 Sa to 16 MSa (maximum).

Parameters:

- **arb_name** – Trace name stored in volatile memory. Use this name when accessing the trace.

- **data_points** – Individual trace samples. The format parameter selects the representation. format = ‘DAC’ (default): accepts a list of integer values from -32767 to +32767, with at least 8 and no more than 65536 points. format = ‘float’: accepts floating point list entries from -1.0 to +1.0, with at least 8 and no more than 65536 points. format = ‘binary’: accepts 8 bit data supplied as a binary stream.

- **data_format** – Specifies the data_points representation. Allowed values are ‘DAC’ (default), ‘float’ or ‘binary’. See the data_points parameter documentation above. (default: `'DAC'`)
