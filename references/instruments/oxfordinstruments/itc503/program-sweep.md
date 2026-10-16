# pymeasure.instruments.oxfordinstruments.ITC503.program_sweep

[Owning PyMeasure class, adapter and connection contract](overview.md)

program_sweep(*temperatures*, *sweep_time*, *hold_time*, *steps=None*)

Programs a temperature sweep in the controller and stops any sweep already running. Once the sweep has been programmed, start it with OxfordITC503.sweep_status = 1.

Parameters:

- **temperatures** - Array containing the temperatures used for the sweep

- **sweep_time** - Time, or array of times, for sweeping to a set-point in minutes (between 0 and 1339.9).

- **hold_time** - Time, or array of times, to remain at a set-point in minutes (between 0 and 1339.9).

- **steps** - Number of steps in the sweep; when supplied, temperatures, sweep_time and hold_time are interpolated into approximately equal segments (default: `None`)
