# pymeasure.instruments.advantest.advantestR624X.SMUChannel.set_output_type

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_output_type(*output_type*, *measurement_type*)

Configure the output method and GPIB output type (`OFM`).

Parameters:

- **output_type** (int or `OutputType`) – Property controlling the output type

- **measurement_type** (int or `MeasurementType`) – Property controlling the measurement type

Note

For output data formatting, see `AdvantestR624X.set_output_format()`. DC and pulse measurements always use output method ‘1’ (real-time output). If output method ‘3’ (buffering output) is specified, measured data is not stored in memory.
