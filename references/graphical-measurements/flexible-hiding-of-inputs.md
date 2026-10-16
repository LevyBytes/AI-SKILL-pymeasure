# Flexible hiding of inputs

Some procedures need to hide or show several inputs, for instance when a measurement branch is skipped after a single `BooleanParameter` changes state. In that situation, a `Parameter` can be tied to a controlling `Parameter`; the `Input` for the controlled `Parameter` is shown or hidden according to the controlling value. Configure this relationship with the `group_by` key-word argument.

```python
from pymeasure.experiment.parameters import BooleanParameter, FloatParameter

toggle = BooleanParameter("toggle", default=True)
param = FloatParameter('some parameter', group_by='toggle')

```

When `toggle` and `param` are both shown in the `InputsWidget` (for example via `inputs=['iterations', 'delay', 'seed']` above), the checkbox for `toggle` controls whether the input-field of `param` is displayed. By default, a group is shown when the `group_by` `Parameter` evaluates to `True`; this default mainly matters for a `BooleanParameter`. Other matching values can be supplied through the `group_condition` keyword argument.

```python
from pymeasure.experiment.parameters import FloatParameter, IntegerParameter

iterations = IntegerParameter('Loop Iterations', default=100)
param = FloatParameter('some parameter', group_by='iterations', group_condition=99)

```

With this setup, the input of `param` appears only when `iterations` equals 99. Any `Parameter` type can serve as the `group_by` `Parameter`.

Further customization is available by using a (lambda)function as the condition:

```python
from pymeasure.experiment.parameters import FloatParameter, IntegerParameter

iterations = IntegerParameter('Loop Iterations', default=100)
param = FloatParameter('some parameter', group_by='iterations', group_condition=lambda v: 50 < v < 100)

```

Here, the input of `param` is displayed only when `iterations` has a value from 51 through 99.

Set the `ManagedWindow` keyword-argument `hide_groups` to choose the behavior: `hide_groups = True` hides grouped inputs, while `hide_groups = False` leaves them disabled / grayed-out.

You may also pass several parameters to `group_by`. In that form, the input is displayed only when every condition is true. Multiple grouping parameters can be supplied as a dict mapping strings to conditions, or as a list of parameter-name strings; for the list form, `group_condition` may be one condition or a list of conditions:

```python
from pymeasure.experiment.parameters import BooleanParameter, FloatParameter, IntegerParameter

iterations = IntegerParameter('Loop Iterations', default=100)
toggle = BooleanParameter('A checkbox')
param_A = FloatParameter('some parameter', group_by=['iterations', 'toggle'], group_condition=[lambda v: 50 < v < 100, True])
param_B = FloatParameter('some parameter', group_by={'iterations': lambda v: 50 < v < 100, 'toggle': True})

```

In this example, `param_A` and `param_B` use the same grouping rules: both are visible only when `iterations` is from 51 to 99 and the toggle checkbox is checked (i.e. True).
