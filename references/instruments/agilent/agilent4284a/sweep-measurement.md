# pymeasure.instruments.agilent.Agilent4284A.sweep_measurement

[Owning PyMeasure class, adapter and connection contract](overview.md)

sweep_measurement(*sweep_mode*, *sweep_values*)

Performs list sweep measurement with a sequential trigger.

Parameters:

- **sweep_mode** (*str*) - parameter selected for sweeping. Valid choices are frequency, voltage, current, bias_voltage, and bias_current.

- **sweep_values** - list containing the parameter values used for the sweep.

Returns:

values configured with `impedance_mode`, together with sweep parameters formatted as ([val A], [val B], [sweep_values])
