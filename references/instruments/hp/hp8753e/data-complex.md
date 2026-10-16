# pymeasure.instruments.hp.HP8753E.data_complex

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *data_complex

Read the complex s-parameter measurements from the most recent scan. The call blocks until completion.

Parameters:

**timeout** - Optional wait value in seconds before timing out. (default: `10`)

Raises:

**TimeoutError** - Raised when the VNA does not complete the sweep before timeout occurs.

Returns:

Returns an array of s-parameters for the measurement_parameter.

Return type:

numpy.ndarray
