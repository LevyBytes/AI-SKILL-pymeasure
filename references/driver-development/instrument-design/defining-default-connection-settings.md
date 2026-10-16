# Defining default connection settings

Instrument implementations sometimes need default connection settings. Reasons include a connection that needs *specific non-default settings* or an instrument that supports *multiple interfaces*.

[`VISAAdapter`](https://pymeasure.readthedocs.io/en/latest/api/adapters.html#pymeasure.adapters.VISAAdapter) supports handling connection settings flexibly inside the instrument initializer.
