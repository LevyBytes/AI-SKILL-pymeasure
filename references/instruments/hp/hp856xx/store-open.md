# pymeasure.instruments.hp.hp856Xx.HP856Xx.store_open

HP856Xx.store_open()

Store the current instrument state and trace A in nonvolatile memory.

Use this command together with `store_short()`, and run it before `store_short()`. Data captured during the store open procedure is averaged with data captured during `store_short()` to create an open/short calibration. For the calibration to remain valid, the instrument state, meaning the instrument settings, must not change between `store_open()` and `store_short()`. See the `store_short()` command description for additional details.
