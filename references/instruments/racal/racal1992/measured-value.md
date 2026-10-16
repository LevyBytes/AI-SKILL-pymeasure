# pymeasure.instruments.racal.Racal1992.measured_value

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *measured_value

Get measured value.

A Racal-Dana 1992 does not send measurement data in direct response to a measurement-data request. Instead, completed measurements are pushed into a FIFO; once that FIFO is full, the oldest measurement is discarded.

The FIFO buffer is emptied when the instrument receives a command needing an immediate reply, such as reading a setting. Clearing an operating mode also empties it.

If no measurement data is present, this property blocks until data arrives. It can also timeout after the interval configured through the standard pyvisa API.

To ensure measurement data exists first, call wait_for_measurement().
