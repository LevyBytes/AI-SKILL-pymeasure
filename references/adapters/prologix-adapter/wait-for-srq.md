# pymeasure.adapters.PrologixAdapter.wait_for_srq

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_srq(*timeout=25*, *delay=0.1*)

Waits for a SRQ and keeps the bit asserted.

Parameters:

- **timeout** – Timeout interval in seconds. (default: `25`)

- **delay** – Delay between SRQ checks, in seconds. (default: `0.1`)

Raises:

**TimeoutError** – raises “Waiting for SRQ timed out.”
