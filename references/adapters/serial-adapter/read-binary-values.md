# pymeasure.adapters.SerialAdapter.read_binary_values

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_binary_values(*header_bytes=0*, *termination_bytes=None*, *dtype=<class 'numpy.float32'>*, *sep=''*, ***kwargs*)

Produces a numpy array from the response to a binary-data query.

Parameters:

- **header_bytes** (*int*) – Byte count at the message header to skip.

- **termination_bytes** (*int*) – Byte count to remove from the message tail, or None.

- **dtype** – NumPy dtype used when formatting the resulting values. (default: `<class 'numpy.float32'>`)

- **sep** (*string*) – Character separator; when provided, fromstring is used, otherwise frombytes is used.

- ****kwargs** – Additional parameters supplied to the NumPy fromstring / frombytes method.

Returns:

NumPy array of values

Raises:

**ValueError** – raised when the data buffer is empty or malformed
