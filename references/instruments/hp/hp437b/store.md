# pymeasure.instruments.hp.HP437B.store

[Owning PyMeasure class, adapter and connection contract](overview.md)

store(*register*)

The power meter can save instrument configurations for later recall. These values can be stored in the internal registers:

- reference calibration factor value

- Measurement units (dBm or watts)

- relative value plus status (on or off)

- power reference status (on or off)

- calibration factor value

- SENSOR ID (sensor data table selection)

- offset value plus status (on or off)

- range (Auto or Set)

- frequency value

- resolution

- duty cycle value plus status (on or off)

- Filter setting (number of readings averaged, auto or manual)

- Limits value plus status (on or off)

Instrument configurations can be stored in registers 1 through 10.
