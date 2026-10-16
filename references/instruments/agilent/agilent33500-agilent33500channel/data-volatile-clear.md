# pymeasure.instruments.agilent.agilent33500.Agilent33500Channel.data_volatile_clear

[Owning PyMeasure class, adapter and connection contract](overview.md)

data_volatile_clear()

Remove all arbitrary signals from a channel's volatile memory.

Use this before repeatedly writing different arbitrary signals under the same name; loading a trace that is already present in memory raises an error.
