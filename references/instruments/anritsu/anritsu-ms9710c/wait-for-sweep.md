# pymeasure.instruments.anritsu.AnritsuMS9710C.wait_for_sweep

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_sweep(*n=20*, *delay=0.5*)

Block until a sweep stops.

Checks bit 1 of the ESR2 to perform this.
