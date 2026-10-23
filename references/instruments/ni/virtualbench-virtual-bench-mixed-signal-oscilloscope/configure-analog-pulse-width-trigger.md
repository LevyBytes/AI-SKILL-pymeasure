# pymeasure.instruments.ni.virtualbench.VirtualBench.MixedSignalOscilloscope.configure_analog_pulse_width_trigger

[Owning MixedSignalOscilloscope contract](overview.md)

configure_analog_pulse_width_trigger(*trigger_source*, *trigger_polarity*, *trigger_level*, *comparison_mode*, *lower_limit*, *upper_limit*, *trigger_instance*)

Creates an analog pulse-width trigger for the requested source; the edge must hit the configured levels within the configured time window.

Parameters:

- **trigger_source** (*str*) – Channel string

- **trigger_polarity** (*int** or **str*): Trigger slope selection (`'POSITIVE'` or `'NEGATIVE'`)

- **trigger_level** (*float*) – Trigger level

- **comparison_mode** (*int** or **str*): Comparison mode (`'GREATER_THAN_UPPER_LIMIT'`, `'LESS_THAN_LOWER_LIMIT'`, `'INSIDE_LIMITS'` or `'OUTSIDE_LIMITS'`)

- **lower_limit** (*float*) – Lower limit

- **upper_limit** (*float*) – Upper limit

- **trigger_instance** (*int** or **str*): Trigger instance
