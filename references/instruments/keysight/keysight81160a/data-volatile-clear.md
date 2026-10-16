# pymeasure.instruments.keysight.Keysight81160A.data_volatile_clear

[Owning PyMeasure class, adapter and connection contract](overview.md)

data_volatile_clear()

Remove all arbitrary signals from volatile memory.

Use this when repeatedly loading different arbitrary signals under the same name, because loading a trace whose name already exists in memory will produce an error.
