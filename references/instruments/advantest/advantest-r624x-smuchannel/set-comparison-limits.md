# pymeasure.instruments.advantest.advantestR624X.SMUChannel.set_comparison_limits

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_comparison_limits(*comparison*, *voltage_value*, *upper_limit*, *lower_limit*)

Configure measurement comparison ON/OFF and the upper/lower limit values (`CMD`).

Parameters:

- **comparison** (*bool*) – Boolean setting that enables or disables the comparison function. Valid values are True or False.

- **voltage_value** (*bool*) – Boolean setting that selects whether voltage or current values are passed. Valid values are True or False.

- **upper_limit** (*float*) – Numeric upper comparison limit

- **lower_limit** (*float*) – Numeric lower comparison limit
