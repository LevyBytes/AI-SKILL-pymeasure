# pymeasure.instruments.hp.HP437B.activate_auto_range

[Owning PyMeasure class, adapter and connection contract](overview.md)

activate_auto_range()

For each sensor, the power meter splits the power range into 5 ranges, each 10 dB wide. Range 1 handles the highest sensitivity and lowest power levels, while Range 5 is the lowest sensitivity and highest power levels. If a sensor spans less than 50 dB, Range 5 may be under 10 dB. Range selection supports both automatic and manual control. `activate_auto_range` chooses the correct range automatically for the present measurement.
