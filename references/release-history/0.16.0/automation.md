# Version 0.16.0 (2026-05-20) - Automation

- The qtpy dependency was added for Qt version shimming (@Benbriel, #1285).

- Add `description` to `Parameters` (@Benbriel, #1211)

- Procedures now emit results in batches (@jvdoorn, #1256).

- Numeric constants were replaced with the corresponding Qt enum values (@dl8dtl, #1265).

- Removed `np.fromstring(sep="")` usage was replaced with `np.frombuffer` (@BenediktBurger, #1330).

- BooleanParameter now accepts numpy.bool (@Falk3579, #1373).

- Workers now check should_stop after `startup()` before execute() runs (@breakU1, #1445).

- Add vector parameter input (@Falk3579, #1376, #1377, #1382)

- `load_module()` was replaced by `exec_module()` (@Falk3579, #1415).

- `Results.data` now checks file size and skips reading when the data file has not changed (@mcdo0486, #1429).
