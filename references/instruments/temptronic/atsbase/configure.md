# pymeasure.instruments.temptronic.ATSBase.configure

[Owning PyMeasure class, adapter and connection contract](overview.md)

configure(*temp_window=1*, *dut_type='T'*, *soak_time=30*, *dut_constant=100*, *temp_limit_air_low=-60*, *temp_limit_air_high=220*, *temp_limit_air_dut=50*, *maximum_test_time=1000*)

Helper for the key configuration properties.

Parameters:

- **dut_type** - string: selects which DUT type to use (default: `'T'`)

- **soak_time** - float: elapsed time in soak_window before settling is reported (default: `30`)

- **soak_window** - float: Soak window size, also used as the temperature settling bounds (K)

- **dut_constant** - float: DUT time constant; higher values indicate higher thermal mass (default: `100`)

- **temp_limit_air_low** – float: minimum flow temperature limit (°C) (default: `-60`)

- **temp_limit_air_high** – float: maximum flow temperature limit (°C) (default: `220`)

- **temp_limit_air_dut** - float: maximum allowed DUT-to-Flow temperature difference (K) (default: `50`)

- **maximum_test_time** - float: maximum test time (seconds) for one temperature point, used as safety limit (default: `1000`)

Returns:

self
