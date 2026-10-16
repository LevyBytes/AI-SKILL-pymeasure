# pymeasure.instruments.eurotest.EurotestHPP120256.shutdown

[Owning PyMeasure class, adapter and connection contract](overview.md)

shutdown(*voltage_rate=200.0*)

Change the output voltage setting (V) to zero, and change the output-voltage ramp speed, voltage_rate (V/s). After shutdown is called, if the HV voltage output > 0, it should fall to zero at the rate given by the voltage_rate parameter. :type voltage_rate: :param voltage_rate: changing rate (V/s) for the voltage output (default: `200.0`)
