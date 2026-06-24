# Instruments — Instruments (part 2)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

Byte response from the instrument, with termination included.

Return type:

`bytes`

 wait_for(*query_delay=None*)

Pause for a specified time; â€˜askâ€™ uses this interval before reading.

Parameters:

**query_delay** (`Optional`[`float`]) â€“ Seconds to pause after writing before reading. `None` uses the default delay. (default: `None`)

Return type:

`None`

 write(*command*, ***kwargs*)

Send a string command to the instrument with write_termination appended.

Parameters:

-

**command** (`str`) â€“ command string sent to the instrument. The channel id replaces â€˜{ch}â€™.

-

**kwargs** â€“ Keyword arguments passed to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Send binary values to the instrument.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) â€“ Values that will be transmitted.

-

****kwargs** (**args**,*) â€“ Additional arguments passed on to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Transmit the bytes content to the instrument.

Return type:

`None`

 *class *pymeasure.instruments.fakes.FakeInstrument(*adapter=None*, *name='Fake Instrument'*, *includeSCPI=False*, ***kwargs*)

Bases: `Instrument`

Supplies a fake implementation of the Instrument class for use in tests.

 *static *control(*get_command*, *set_command*, *docs*, *validator=<function FakeInstrument.<lambda>>*, *values=()*, *map_values=False*, *get_process=<function FakeInstrument.<lambda>>*, *set_process=<function FakeInstrument.<lambda>>*, *check_set_errors=False*, *check_get_errors=False*, ***kwargs*)

Fake Instrument.control.

Remove command text, then store and return only the values selected by format strings, emulating many simple commands. This matches the handling used by tests in test_instrument.

 *class *pymeasure.instruments.fakes.SwissArmyFake(*name='Mock instrument'*, *wait=0.1*, ***kwargs*)

Bases: `FakeInstrument`

Dummy instrument class intended for tests.

The class is a Swiss Army knife for fake data, offering streams in multiple forms. At present, generated streams include â€˜voltagesâ€™, sinusoidal â€˜waveformsâ€™, and mono channel â€˜image dataâ€™.

 *property *frame

Get a new image frame.

 *property *frame_format

Choose the image-data format returned by the get_frame() method: use mono_8 for a single channel 8-bit image, or mono_16 for a single channel 16-bit image.

 *property *frame_height

Control frame height in pixels.

 *property *frame_width

Control frame width in pixels.

 *property *output_voltage

Control the voltage.

 *property *time

Control the elapsed time.

 *property *voltage

Measure the voltage.

 *property *wave

Measure a waveform.
