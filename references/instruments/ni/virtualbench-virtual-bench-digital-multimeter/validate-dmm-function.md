# pymeasure.instruments.ni.virtualbench.VirtualBench.DigitalMultimeter.validate_dmm_function

[Owning DigitalMultimeter contract](overview.md)

validate_dmm_function(*dmm_function*)

Determine whether DMM function *dmm_function* is available

Parameters:

**dmm_function** (*int** or **str*) –

DMM function index or name:

- `'DC_VOLTS'`, `'AC_VOLTS'`

- `'DC_CURRENT'`, `'AC_CURRENT'`

- `'RESISTANCE'`

- `'DIODE'`

Returns:

DMM function index supplied to the instrument

Return type:

int
