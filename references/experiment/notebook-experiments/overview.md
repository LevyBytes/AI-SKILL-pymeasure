# pymeasure.experiment.experiment.Experiment

*class *pymeasure.experiment.experiment.Experiment(*title*, *procedure*, *analyse=<function Experiment.&lt;lambda&gt;>*)

Bases: `object`

Class that starts logging and creates/runs the results and worker processes.

The following notebook example supplies a concrete Procedure and data columns. It creates two plots before entering the live-update loop.

```python
from time import sleep
import matplotlib.pyplot as plt
from pymeasure.experiment import Procedure
from pymeasure.experiment.experiment import Experiment

class DemoProcedure(Procedure):
    DATA_COLUMNS = ['x', 'y', 'z']

    def execute(self):
        for x in range(100):
            if self.should_stop():
                break
            self.emit('results', {'x': x, 'y': x * 2, 'z': x * x})
            sleep(0.1)

experiment = Experiment('demo', DemoProcedure())
experiment.start()
figure, axes = plt.subplots(1, 2)
experiment.plot('x', 'y', ax=axes[0])
experiment.plot('x', 'z', ax=axes[1])
experiment.plot_live()
```

For one plot, use `experiment.plot_live('x', 'y', style='.-')` instead of the subplot setup and final call. Use a notebook plotting backend suitable for live updates.

Variables:

**value** - The parameter value

Parameters:

- **title** – The experiment title

- **procedure** – The procedure object

- **analyse** - Post-analysis function that receives a pandas dataframe and returns it with added analysed columns. Analysed results are exposed through experiment.data; raw data remains available through experiment.results.data. (default: `<function Experiment.<lambda>>`)

- **_data_timeout** - Time limit controlling how long live plotting waits for datapoints.
