# pymeasure.instruments.racal.Racal1992.wait_for_measurement

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_measurement(*timeout=None*, *progressDots=False*)

Wait until a fresh measurement is ready.

Parameters:

- **timeout** – seconds to wait before raising the timeout exception. (default: `None`)

- **progressDots** – if true, print ‘.’ after every ready-check (default: `False`)
