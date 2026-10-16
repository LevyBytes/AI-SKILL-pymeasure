# pymeasure.instruments.agilent.agilentB1500.AgilentB1500.read_data

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_data(*number_of_points*)

Read the full buffer and return the contents as a Pandas DataFrame.

Provide the measurement-point count so the data list can be split correctly.

Parameters:

**number_of_points** (*int*) – Count of measurement points

Returns:

Measurement Data

Return type:

pd.DataFrame
