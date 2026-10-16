# pymeasure.instruments.tcpowerconversion.CXN.Status

[Owning PyMeasure class, adapter and connection contract](../cxn/overview.md)

*class *Status(**values*)

Bases: `IntFlag`

IntFlag type that represents the CXN status.

The status bits map as follows: bit 14 indicates Analog interface enabled; bit 11 indicates Interlock open; bit 10 indicates Over temperature; bit 9 indicates Reverse power limit; bit 8 indicates Forward power limit; bit 6 indicates MCG mode active; bit 5 indicates load power leveling active; bit 4 indicates External RF source active; bit 0 indicates RF power on.
