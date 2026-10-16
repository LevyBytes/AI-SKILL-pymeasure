# pymeasure.instruments.eurotest.EurotestHPP120256.wait_for_output_voltage_reached

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_output_voltage_reached(*voltage_setpoint*, *abs_output_voltage_error=0.03*, *check_period=1.0*, *timeout=60.0*)

Wait until the HV voltage output reaches the voltage setpoint.

At each check_period-second interval, measure the voltage output; raise an exception if the voltage output does not reach the voltage setting before timeout expires. :type voltage_setpoint: :param voltage_setpoint: voltage in kVolts set in the HV power supply that should appear at the output after some time, depending on the ramp setting. :type abs_output_voltage_error: :param abs_output_voltage_error: absolute error in kVolts for considering the output voltage reached (default: `0.03`). :type check_period: :param check_period: period, in seconds, between voltage output measurements. (default: `1.0`) :type timeout: :param timeout: allowed duration, in seconds, for reaching the voltage setting at the output. (default: `60.0`) :return: None :raises: Exception when timeout finishes (seconds) before the voltage output reaches the voltage setting.
