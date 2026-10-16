# pymeasure.instruments.hp.HP8753E.scan

[Owning PyMeasure class, adapter and connection contract](overview.md)

scan(*timeout=10*)

Start a scan using the specified number of averages and block until completion.

Parameters:

**timeout** - Optional seconds added to the sweep time before timing out. (default: `10`)

Raises:

**TimeoutError** - Raised when the VNA does not complete the sweep before timeout occurs.

Returns:

None.
