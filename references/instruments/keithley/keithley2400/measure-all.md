# pymeasure.instruments.keithley.Keithley2400.measure_all

[Owning PyMeasure class, adapter and connection contract](overview.md)

measure_all()

Acquire current (A), voltage (V), resistance (Ohm), time (s), and status in one operation.

Note

Also sets `resistance_mode_auto` to False

### Returns

dict

Dictionary containing these keys: - ?current? (float): current in A. - ?voltage? (float): voltage in V. - ?resistance? (float): resistance in Ohms. - ?time? (float): elapsed time in s. - ?status? (int): status flag from the instrument.
