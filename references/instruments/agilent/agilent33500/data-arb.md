# pymeasure.instruments.agilent.Agilent33500.data_arb

[Owning PyMeasure class, adapter and connection contract](overview.md)

data_arb(*arb_name*, *data_points*, *data_format='DAC'*)

Loads an arbitrary trace into device volatile memory.

data_points accepts three encodings: 16 bit DAC entries separated by commas (ranging from -32767 to +32767), floating point entries separated by commas (ranging from -1.0 to +1.0), or a binary data stream. Consult the manual for fuller details. Storage is model-dependent and spans 8 Sa to 16 MSa (maximum).

Parameters:

- **arb_name** – Name assigned to the trace in volatile memory; use it later to select that trace.

- **data_points** – Trace sample values. Interpretation is selected by the format parameter. format = ‘DAC’ (default): accepts integer lists from -32767 to +32767. Requires at least 8 and at most 65536 points. format = ‘float’: accepts floating point lists from -1.0 to +1.0. Requires at least 8 and at most 65536 points. format = ‘binary’: accepts an 8 bit binary stream.

- **data_format** – Chooses how data_points is interpreted. Valid values are ‘DAC’ (default), ‘float’ or ‘binary’. See the data_points parameter description above. (default: `'DAC'`)
