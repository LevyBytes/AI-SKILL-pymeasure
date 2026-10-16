# pymeasure.instruments.oxfordinstruments.IPS120_10.train_magnet

[Owning PyMeasure class, adapter and connection contract](overview.md)

train_magnet(*training_scheme*)

Trains the magnet after cooling down, then returns the field to 0 tesla using the last-used ramp-rate.

Parameters:

**training_scheme** - Training schedule given as a list of tuples; every tuple contains a (field [T], ramp-rate [T/min]) pair.
