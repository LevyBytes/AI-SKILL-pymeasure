# pymeasure.instruments.keithley.Keithley2281S.characterize

[Owning PyMeasure class, adapter and connection contract](overview.md)

characterize(*lower_voltage*, *upper_voltage*, *charge_current*, *memory_slot*, *model_voltage_offset=0.05*, *charge_delay=0*)

Convenience routine for running a battery test and storing its model in internal memory.

The device discharges only at a fixed 1A. When that current is too high, place a series resistor in the discharge path to limit it. If discharge goes below the lower limit, the instrument charges at a 10th of the set charge current until the lower limit is reached, and only then characterizes the battery profile. This call blocks until measurement completion.

Parameters:

- **lower_voltage** (*float*) – Discharge stop voltage; choose a value slightly lower (~0.05V) than normal operation.

- **upper_voltage** (*float*) – Charge stop voltage; choose a value slightly higher (~0.05V) than normal operation.

- **charge_current** (*float*) – Maximum charge current. The (dis-)charge end current is 1/100th of this value.

- **memory_slot** (*int*) – Internal memory slot where the model is saved

- **model_voltage_offset** (*float**, **optional*) – Offset applied to the generated model upper and lower voltage limits. The limits must remain inside the measured values, between the hard measurement limits. Default is 0.05. (default: `0.05`)

- **charge_delay** (*float**, **optional*) – Wait time in seconds between discharge and charge phases. The real elapsed time is longer because the device delays reporting test completion internally. Default is 0. (default: `0`)
