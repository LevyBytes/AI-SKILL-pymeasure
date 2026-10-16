# pymeasure.adapters.FakeAdapter.read_binary_values

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_binary_values(*header_bytes=0*, *termination_bytes=None*, *dtype=<class 'numpy.float32'>*, *sep=''*, ***kwargs*)

Return a numpy array produced by querying binary data.

Parameters:

- **header_bytes** (*int*) - Count of header bytes to ignore.

- **termination_bytes** (*int*) - Count of bytes to remove from the message end, or None.

- **dtype** - NumPy data type used to format the values. (default: `<class 'numpy.float32'>`)

- **sep** (*string*) - Character separator. If provided, use fromstring; otherwise use frombytes.

- ****kwargs** - Additional arguments for the NumPy fromstring / frombytes method.

Returns:

NumPy array of values

Raises:

**ValueError** - when the data buffer is empty or malformed
