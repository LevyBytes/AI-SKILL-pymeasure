# pymeasure.instruments.keysight.KeysightPNA.data_format

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *data_format*: Any*

Control `data_format`, limited strictly to `ascii`, `real32`, or `real64`.

- `ascii` is slow; choose it only when small amounts data must be transferred.

- `real32` works best for large measurement-data transfers. It may introduce rounding errors in frequency data.

- `real64` is slower than `real32` and provides more significant digits. Accurate frequency data representation requires it.

On the PNA, measurement data is kept as 32 bit and frequencies as 64 bit. Use `real32` for data and `real64` for frequencies so precision is not lost while data transfer stays as fast as possible.

Note

Running [`reset()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument.reset) changes `data_format` back to `ascii`.
