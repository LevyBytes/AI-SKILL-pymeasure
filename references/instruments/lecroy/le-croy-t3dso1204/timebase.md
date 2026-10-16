# pymeasure.instruments.lecroy.LeCroyT3DSO1204.timebase

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *timebase

Return the timebase setup as a dict with these keys:

- `timebase_scale`: seconds/div horizontal scale (float)

- `timebase_offset`: seconds between the trigger and reference position (float)

- `timebase_hor_magnify`: zoom-window horizontal scale in seconds/div (float)

- `timebase_hor_position`: zoom-window horizontal position in seconds (float)
