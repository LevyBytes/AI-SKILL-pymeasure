# pymeasure.instruments.danfysik.Danfysik8500.sync_sequence

[Owning PyMeasure class, adapter and connection contract](overview.md)

sync_sequence(*stack*, *delay=0*)

Arm the ramp sequence for triggering by hardware input to pin P33 1&2 (10 to 24 V) or by a TS command. When delay is supplied, the sequence begins after that delay.

Parameters:

- **stack** (`int`) – Stack number in the range 0-15

- **delay** – Delay time in seconds (default: `0`)

Return type:

`None`
