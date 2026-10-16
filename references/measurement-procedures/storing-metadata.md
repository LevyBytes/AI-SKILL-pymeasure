# Storing metadata

Metadata ([`pymeasure.experiment.parameters.Metadata`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#pymeasure.experiment.parameters.Metadata)) stores measurement information, such as the actual starting time or instrument parameters, in the datafile header. Metadata objects are evaluated and written only after the `startup` method completes, so startup can query an instrument and then place those settings in the file. Metadata is almost as simple to use as a Parameter; the previous example can be extended with metadata as follows:

```python
from time import sleep, time
from pymeasure.experiment import Procedure
from pymeasure.experiment import IntegerParameter, Metadata

class SimpleProcedure(Procedure):

    # a Parameter that defines the number of loop iterations
    iterations = IntegerParameter('Loop Iterations')

    # the Metadata objects store information after the startup has ran
    starttime = Metadata('Start time', fget=time)
    custom_metadata = Metadata('Custom', default=1)

    # a list defining the order and appearance of columns in our data file
    DATA_COLUMNS = ['Iteration']

    def startup(self):
        self.custom_metadata = 20

    def execute(self):
        """ Loops over each iteration and emits the current iteration,
        before waiting for 0.01 sec, and then checking if the procedure
        should stop
        """
        for i in range(self.iterations):
            self.emit('results', {'Iteration': i})
            sleep(0.01)
            if self.should_stop():
                break

```

Like a Parameter, PyMeasure replaces Metadata with their values behind the scenes, making Metadata values straightforward to access.

A Metadata value can come from an `fget` method or be assigned manually inside the startup method. If fget is supplied, it runs after startup method. `fget` may also be a string; then the string is interpreted as the name of a Procedure class attribute, callable or not, whose value should be stored. Nested attributes are supported by separating names with a period, which is useful for recording an instrument property or method. Examples include instrument_name.attribute_name and instrument_name.subclass_name.attribute_name. In that dotted form, only the last element, such as attribute_name, may refer to a callable. If no `fget` method is supplied and no value is assigned manually, Metadata falls back to its default value when one exists. The fmt argument controls formatting for the Metadata-object value.
