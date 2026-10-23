# pymeasure.instruments.advantest.advantestR624X.seq_sample_mode

[Owning PyMeasure class, adapter and connection contract](../advantest-r624x-sequence-wait-mode/overview.md)

pymeasure.instruments.advantest.advantestR624X.seq_sample_mode(*mode*, *auto_sampling=True*, *channel=1*)

Create the command string for JM (sample mode).

Parameters:

- **mode** (int or `SampleMode`): Sample mode selection.

- **auto_sampling** (*bool*): Controls auto sampling. With True, each trigger automatically returns measurement data. With False, data is returned only after an explicit request such as `FCH?`. For dual-channel synchronous modes (`PULSED_SYNC`, `SWEEP_SYNC`, etc.), use False so the returned values are the actual measurement results.

- **channel** (*int*): Channel identifier (1=A, 2=B).

Return type:

str
