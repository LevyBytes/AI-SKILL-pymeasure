# pymeasure.instruments.keysight.KeysightPNA

*class *pymeasure.instruments.keysight.KeysightPNA(*adapter*, *name='Keysight PNA'*, *data_format='real64'*, *byte_order_swapped=True*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class for a Keysight PNA vector network analyzer.

Parameters:

- **data_format** (*str*) – set `data_format` only to `ascii`, `real32`, or `real64`.

- **byte_order_swapped** (*bool*) – set `byte_order_swapped` for `real32` or `real64` data formatting.

```python
from pymeasure.instruments.keysight.keysightPNA import KeysightPNA

pna = KeysightPNA("GPIB0::16::INSTR",
                  timeout=5000,
                  )

pna.load_state("D:/States/MyState.csa")
pna.adapter.connection.timeout = 20000  # set a new timeout to 20 sec
pna.ch_1.single()  # execute a single trigger of channel 1
pna.complete  # wait till the sweep has finished
x_data = pna.ch_1.tr_1.x_data  # get the X data of trace 1 in channel 1
y_data = pna.ch_2.tr_5.y_data  # get the Y data of trace 5 in channel 2
y_complex = pna.ch_2.tr_5.y_data_complex  # get the complex Y data of trace 5 in channel 2
pna.ch_1.tr_1.mkr_1.enabled = True  # Activate marker 1 on trace 1 in channel 1
pna.ch_1.tr_1.mkr_1.x = 123e6  # Set marker 1 to 123 MHz
mkr_y = pna.ch_1.tr_1.mkr_1.y  # Read the marker 1 y data

```

Workflow:

- Configure channels/measurements on the PNA directly.

- Calibrate the PNA

- Save the current state as a csa file

- Run single triggers across the different channels.

- Access measurement data by channel number and trace number.
