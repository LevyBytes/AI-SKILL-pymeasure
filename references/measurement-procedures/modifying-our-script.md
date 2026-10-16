# Modifying our script

With the Procedure class features and execution model covered, return to the IV characteristic measurement and rewrite it with Procedures. The example below shows the revised script as a IVProcedure class.

```python
# Import necessary packages
from pymeasure.instruments.keithley import Keithley2400
from pymeasure.experiment import Procedure, Results, Worker
from pymeasure.experiment import IntegerParameter, FloatParameter
from time import sleep
import numpy as np

from pymeasure.log import log, console_log

class IVProcedure(Procedure):

    data_points = IntegerParameter('Data points', default=20)
    averages = IntegerParameter('Averages', default=8)
    max_current = FloatParameter('Maximum Current', units='A', default=0.001)
    min_current = FloatParameter('Minimum Current', units='A', default=-0.001)

    DATA_COLUMNS = ['Current (A)', 'Voltage (V)', 'Voltage Std (V)']

    def startup(self):
        log.info("Connecting and configuring the instrument")
        self.sourcemeter = Keithley2400("GPIB::24")
        self.sourcemeter.reset()
        self.sourcemeter.use_front_terminals()
        self.sourcemeter.apply_current(100e-3, 10.0)  # current_range = 100e-3, compliance_voltage = 10.0
        self.sourcemeter.measure_voltage(0.01, 1.0)  # nplc = 0.01, voltage_range = 1.0
        sleep(0.1)  # wait here to give the instrument time to react
        self.sourcemeter.stop_buffer()
        self.sourcemeter.disable_buffer()

    def execute(self):
        currents = np.linspace(
            self.min_current,
            self.max_current,
            num=self.data_points
        )
        self.sourcemeter.enable_source()
        # Loop through each current point, measure and record the voltage
        for current in currents:
            self.sourcemeter.config_buffer(IVProcedure.averages.value)
            log.info("Setting the current to %g A" % current)
            self.sourcemeter.source_current = current
            self.sourcemeter.start_buffer()
            log.info("Waiting for the buffer to fill with measurements")
            self.sourcemeter.wait_for_buffer()
            data = {
                'Current (A)': current,
                'Voltage (V)': self.sourcemeter.means[0],
                'Voltage Std (V)': self.sourcemeter.standard_devs[0]
            }
            self.emit('results', data)
            sleep(0.01)
            if self.should_stop():
                log.info("User aborted the procedure")
                break

    def shutdown(self):
        self.sourcemeter.shutdown()
        log.info("Finished measuring")

if __name__ == "__main__":
    console_log(log)

    log.info("Constructing an IVProcedure")
    procedure = IVProcedure()
    procedure.data_points = 20
    procedure.averages = 8
    procedure.max_current = -0.001
    procedure.min_current = 0.001

    data_filename = 'example.csv'
    log.info("Constructing the Results with a data file: %s" % data_filename)
    results = Results(procedure, data_filename)

    log.info("Constructing the Worker")
    worker = Worker(results)
    worker.start()
    log.info("Started the Worker")

    log.info("Joining with the worker in at most 1 hr")
    worker.join(timeout=3600)  # wait at most 1 hr (3600 sec)
    log.info("Finished the measurement")

```

Parentheses in `COLUMN` entries declare the physical unit for that column. For example, `'Voltage Std (V)'` declares Volts. For a dimensionless value such as Mach number, use (1). Compound units such as (m/s) or the long form (meter/second) are accepted too. The class `Results` stores data using the declared unit; in this case the unit is Volts. A `pint.Quantity` of 500 mV, for instance, is stored as 0.5 V. Strings are converted to a Quantity first, while plain numbers such as float or int are treated as already using the correct unit. Thus 5 is stored as 5 V. If a value is incompatible, either because its unit is wrong, such as meters for a voltage column, or because the value is not numeric, a warning is logged and ‘nan’ is written to the file. When no unit is given, meaning there are no parentheses, that column is not unit-checked unless a Quantity is later provided for it. In that case, the column unit becomes the base unit of the supplied value, such as meter for a value in kilometers, and later entries in the column are unit-checked. Use columns without unit checks, meaning without parentheses, for strings or booleans as well.

You now know how to build a Procedure sub-class. The next section uses those procedures in a graphical environment with live-plotting and simple queuing for multiple experiments. Those capabilities come from the Procedure object.
