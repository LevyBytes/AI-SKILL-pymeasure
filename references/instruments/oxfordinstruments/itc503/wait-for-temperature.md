# pymeasure.instruments.oxfordinstruments.ITC503.wait_for_temperature

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_temperature(*error=0.01*, *timeout=3600*, *check_interval=0.5*, *stability_interval=10*, *thermalize_interval=300*, *should_stop=<function ITC503.&lt;lambda&gt;>*)

Waits until the ITC reaches the set-point temperature.

Parameters:

- **error** - Maximum Kelvin error below which the temperature is treated as being at set-point (default: `0.01`)

- **timeout** - Maximum duration allowed for waiting. Exceeding timeout raises TimeoutError. If timeout is None, no timeout is applied. (default: `3600`)

- **check_interval** - Time between temperature queries sent to the ITC. (default: `0.5`)

- **stability_interval** - Time span during which temperature_error must remain below error for the temperature to count as stable. (default: `10`)

- **thermalize_interval** - Waiting time after stabilization so the system can thermalize. (default: `300`)

- **should_stop** - Optional bool-returning function that can stop the wait before it completes. (default: `<function ITC503.<lambda> at 0x7aa57f5e6fb0>`)
