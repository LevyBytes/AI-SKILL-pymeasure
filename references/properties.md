# Properties

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Writing properties

In PyMeasure, [Python properties](https://docs.python.org/3/howto/descriptor.html#properties) are the standard way to expose variables whose values must be read or assigned.

### The property factories

PyMeasure provides three main convenience factories for class properties: [`CommonBase.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control), [`CommonBase.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement), and [`CommonBase.setting`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.setting). They are also available through the shorter `Instrument.control`, `Instrument.measurement`, and `Instrument.setting` names.

[`Instrument.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement) creates a read-only property for retrieving data from an instrument. Suppose our Extreme 5000 implements `:TEMP?`; the property below can be placed after `def __init__` in the earlier class example, or attached to the class later as shown here:

```python
Extreme5000.cell_temp = Instrument.measurement(
   ":TEMP?",
   """Measure the temperature of the reaction cell.""",
)

```

A documentation string must be supplied; see [Docstrings](https://pymeasure.readthedocs.io/en/latest/dev/coding_standards.html#docstrings) for the relevant convention.

Using this property returns the temperature of the reaction cell.

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.cell_temp  # Sends ":TEMP?" to the device
127.2

```

[`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) builds on that pattern by producing a property that supports both reads and writes. If our Extreme 5000 exposes `:VOLT?` plus `:VOLT <float>` commands expressed in Volts, the property can be written this way.

```python
Extreme5000.voltage = Instrument.control(
    ":VOLT?", ":VOLT %g",
    """Control the voltage in Volts (float)."""
)

```

Here `%g` is the [Python string format](https://docs.python.org/3/library/string.html#format-specification-mini-language) specifier used to pass values through as floating-point text.

With this property, assigning 100 mV sends the correct voltage command; reading it afterwards asks the instrument for the present voltage:

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.voltage = 0.1        # Sends ":VOLT 0.1" to set the voltage to 100 mV
>>> extreme.voltage              # Sends ":VOLT?" to query for the current value
0.1

```

The remaining factory, [`Instrument.setting`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.setting), creates write-only properties.

Together, [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control), [`Instrument.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement), and [`Instrument.setting`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.setting) let instrument classes expose many routine measurement and control points as properties.

The following sections cover other property-factory capabilities: limiting accepted ranges, translating between physical values and command values, and applying heavier processing to data returned by a device.

### Restricting values with validators

Many GPIB/SCPI commands impose tighter limits than the simple examples above. [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) can represent those limits through [`validators`](https://pymeasure.readthedocs.io/en/latest/api/instruments/validators.html#module-pymeasure.instruments.validators). A validator receives a value plus an allowed-value description, then either returns an acceptable value or raises an exception. [`pymeasure.instruments.validators`](https://pymeasure.readthedocs.io/en/latest/api/instruments/validators.html#module-pymeasure.instruments.validators) includes several built-in validators for common cases; the four basic categories are introduced here.

The examples that follow assume the validators have already been imported.

Often the returned string needs parsing before the desired quantity is available, or an outgoing value needs processing before it is sent to the device. [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control), [`Instrument.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement), and [`Instrument.setting`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.setting) include hooks for that work.

### In a restricted range

For range-limited properties, use `strict_range` or `truncated_range`.

For example, when the Extreme 5000 only accepts voltages between -1 V and 1 V, the earlier property can be changed to use a strict validator for that interval.

```python
Extreme5000.voltage = Instrument.control(
    ":VOLT?", ":VOLT %g",
    """Control the voltage in Volts (float strictly from -1 to 1).""",
    validator=strict_range,
    values=[-1, 1]
)

```

With that definition, assigning voltage outside the range raises ValueError.

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.voltage = 100
Traceback (most recent call last):
...
ValueError: Value of 100 is not in range [-1,1]

```

That behavior is useful when invalid input should be surfaced to the programmer. In some drivers, though, clipping the input to the permitted range is more convenient.

```python
Extreme5000.voltage = Instrument.control(
    ":VOLT?", ":VOLT %g",
    """Control the voltage in Volts (float from -1 to 1).

    Invalid voltages are truncated.
    """,
    validator=truncated_range,
    values=[-1, 1]
)

```

This version keeps assignments error-free and clips any out-of-bounds value to the nearest range boundary.

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.voltage = 100  # Executes ":VOLT 1"
>>> extreme.voltage
1.0

```

### In a discrete set

A control property often accepts only a small enumerated set. Use `strict_discrete_set` or `truncated_discrete_set` for that pattern. As with ranges, the strict form raises an error when the submitted value is absent from the set.

For example, suppose the Extreme 5000 provides `:RANG <float>` to choose a voltage range, with valid Volts values of 10 mV, 100 mV, and 1 V. A control property can be defined as follows.

```python
Extreme5000.voltage = Instrument.control(
    ":RANG?", ":RANG %g",
    """Control the voltage range in Volts (float in 10e-3, 100e-3, 1).""",
    validator=truncated_discrete_set,
    values=[10e-3, 100e-3, 1]
)

```

The voltage range can now be assigned, and unsuitable inputs are automatically truncated to a valid choice.

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.voltage = 0.08
>>> extreme.voltage
0.1

```

### Mapping values

After the validators are clear, maps provide another way to satisfy instruments that expect non-physical command values. Enable that behavior with the `map_values` argument of [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control).

When the allowed values are supplied as a list, the command uses the matching list index. For example, if the Extreme 5000 instead expects `:RANG <integer>`, where 0, 1, and 2 mean 10 mV, 100 mV, and 1 V, this control works:

```python
Extreme5000.voltage = Instrument.control(
    ":RANG?", ":RANG %d",
    """Control the voltage range in Volts (float in 10 mV, 100 mV and 1 V).
    """,
    validator=truncated_discrete_set,
    values=[10e-3, 100e-3, 1],
    map_values=True
)

```

In that case, setting 100 mV produces the actual GPIB/SCIP command `:RANG 1`, because 100 mV is at index 1 in the values list.

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.voltage = 100e-3
>>> extreme.read()
'1'
>>> extreme.voltage = 1
>>> extreme.voltage
1

```

Dictionaries make the real-value to instrument-value mapping less constrained. If `:RANG <integer>` instead uses 1, 2, and 3 for 10 mV, 100 mV, and 1 V, replace the previous control with this version.

```python
Extreme5000.voltage = Instrument.control(
    ":RANG?", ":RANG %d",
    """Control the voltage range in Volts (float in 10 mV, 100 mV and 1 V).
    """,
    validator=truncated_discrete_set,
    values={10e-3:1, 100e-3:2, 1:3},
    map_values=True
)

```

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.voltage = 10e-3
>>> extreme.read()
'1'
>>> extreme.voltage = 100e-3
>>> extreme.voltage
0.1

```

Here the dictionary associates each key with a particular value. Keys and values may be any type, which also supports string-valued properties:

```python
Extreme5000.channel = Instrument.control(
    ":CHAN?", ":CHAN %d",
    """Control the measurement channel (string strictly in 'X', 'Y', 'Z').""",
    validator=strict_discrete_set,
    values={'X':1, 'Y':2, 'Z':3},
    map_values=True
)

```

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.channel = 'X'
>>> extreme.read()
'1'
>>> extreme.channel = 'Y'
>>> extreme.channel
'Y'

```

As shown above, validators and maps can make [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) cover substantially more cases.

### Boolean properties

Maps also work well for boolean-style properties, letting the public interface use Pythonic `True` and `False` values:

```python
Extreme5000.output_enabled = Instrument.control(
    "OUTP?", "OUTP %d",
    """Control the instrument output is enabled (boolean).""",
    validator=strict_discrete_set,
    map_values=True,
    values={True: 1, False: 0},  # the dict values could also be "on" and "off", etc. depending on the device
)

```

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.output_enabled = True
>>> extreme.read()
'1'
>>> extreme.output_enabled = False
>>> extreme.output_enabled
False
>>> # Invalid input raises an exception
>>> extreme.output_enabled = 34
Traceback (most recent call last):
...
ValueError: Value of 34 is not in the discrete set {True: 1, False: 0}

```

For boolean property names, choose wording that could answer a yes/no question, such as Is the output enabled? -> `output_enabled`, `display_active`, etc.

### Processing of set values

[`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) and [`Instrument.setting`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.setting) accept the keyword argument set_process. It must be a function that receives the value after validation, transforms it before value mapping, and returns the transformed value. Unit conversion is a typical use, as this example shows:

```python
Extreme5000.current = Instrument.setting(
    ":CURR %g",
    """Set the measurement current in A (float strictly from 0 to 10).""",
    validator=strict_range,
    values=[0, 10],
    set_process=lambda v: 1e3*v,  # convert current to mA
)

```

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.current = 1  # set current to 1000 mA

```

### Processing of return values

[`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) and [`Instrument.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement) likewise accept get_process. When provided, get_process must be a function that receives a value, processes it before value mapping, and returns the result. As with set_process, unit conversion is one use:

```python
Extreme5000.current = Instrument.control(
    ":CURR?", ":CURR %g",
    """Control the measurement current in A (float strictly from 0 to 10).""",
    validator=strict_range,
    values=[0, 10],
    set_process=lambda v: 1e3*v,  # convert to mA
    get_process=lambda v: 1e-3*v,  # convert to A
)

```

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.current = 3.1
>>> extreme.current
3.1

```

set-process and get-process can also convert to or from a `pint.Quantity`. Adapting the previous example to set or return a quantity gives:

```python
from pymeasure.units import ureg

Extreme5000.current = Instrument.control(
    ":CURR?", ":CURR %g",
    """Control the measurement current (float).""",
    set_process=lambda v: v.m_as(ureg.mA),  # send the value as mA to the device
    get_process=lambda v: ureg.Quantity(v, ureg.mA),  # convert to quantity
)

```

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.current = 3.1 * ureg.A
>>> extreme.current.m_as(ureg.A)
3.1

```

Note

At present, this is the way quantities can be handled in pymeasure instruments. [Issue 666](https://github.com/pymeasure/pymeasure/issues/666) is tracking work on a more convenient quantity implementation for the property factories.

get_process is also suitable for text cleanup. For an instrument reply that includes a unit, such as `1.23 nF`, remove the unit before using the number; one implementation is:

```python
Extreme5000.capacity = Instrument.measurement(
    ":CAP?",
    """Measure the capacity in nF (float).""",
    get_process=lambda v: float(v.replace('nF', ''))
)

```

The preprocess_reply keyword argument to [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) or [`Instrument.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement) can perform the same job. This function is passed on to `Adapter.values` and executes immediately after the device reply arrives. Because the built-in casting behavior is then available, the code can be shortened:

```python
Extreme5000.capacity = Instrument.measurement(
    ":CAP?",
    """Measure the capacity in nF (float).""",
    preprocess_reply=lambda v: v.replace('nF', '')
    # notice how we don't need to cast to float anymore
)

```

### Checking the instrument for errors

When a driver must query the instrument's error state separately after a get or set operation, enable the `check_get_errors` and `check_set_errors` parameters of [`control()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control), respectively. After communication with the device finishes, PyMeasure calls [`check_get_errors()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument.check_get_errors) and [`check_set_errors()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument.check_set_errors), respectively. In the default implementation, both methods simply call [`check_errors()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument.check_errors). For instruments that answer every set command with an acknowledgment or error, override [`check_set_errors()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument.check_set_errors) to consume that automatic response.

### Using multiple values

Occasionally one command needs to send or receive several values. [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control) supports this by taking multiple values as a tuple. If the Extreme 5000 sets voltage and frequency through `:VOLTFREQ?` and `:VOLTFREQ <float>,<float>`, the property could look like this:

```python
Extreme5000.combination = Instrument.control(
    ":VOLTFREQ?", ":VOLTFREQ %g,%g",
    """Simultaneously control the voltage in Volts and the frequency in Hertz (both float).

    This property is set by a tuple.
    """
)

```

Using that property, set 200 mV for voltage and 931 Hz for Frequency, then read the pair back right away.

```pycon
>>> extreme = Extreme5000("GPIB::1")
>>> extreme.combination = (0.2, 931)        # Executes ":VOLTFREQ 0.2,931"
>>> extreme.combination                     # Reads ":VOLTFREQ?"
[0.2, 931.0]

```

The interface is awkward, but the pattern is rarely required.

### Dynamic properties

Earlier sections show that Python properties are a compact way to model an instrument's programming interface. PyMeasure adds dynamic property behavior, so subclasses or individual instances can adjust property definitions. This supports several useful cases with little syntax.

To turn on dynamic behavior for a property, set its `dynamic` parameter to `True`.

Once `dynamic` is enabled, specially named attributes, declared on either a class or an instance, can override parameters from the original property definition. Define an attribute named <property name>_<property_parameter> and assign the desired value. Avoid accidentally creating class or instance attributes that match this pattern, because such names may change property behaviour unintentionally.

Note

Because these special attributes should not be confused with ordinary class or instance attributes, they support assignment only and cannot be read.

This dynamic mechanism applies to every property parameter except `dynamic` and `docs`; see [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control), [`Instrument.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement), and [`Instrument.setting`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.setting).

### Dynamic validity range

Consider an instrument whose accepted value range changes with current state. The following code demonstrates that situation using dynamic properties.

```python
Extreme5000.voltage = Instrument.control(
    ":VOLT?", ":VOLT %g",
    """Control the voltage in Volts (float).""",
    validator=strict_range,
    values=[-1, 1],
    dynamic = True,
)
def set_bipolar_mode(self, enabled = True):
    """Safely switch between bipolar/unipolar mode."""

    # some code to switch off the output first
    # ...

    if enabled:
        self.mode = "BIPOLAR"
        # set valid range of "voltage" property
        self.voltage_values = [-1, 1]
    else:
        self.mode = "UNIPOLAR"
        # note the "propertyname_parametername" form of the attribute
        self.voltage_values = [0, 1]

```

The voltage property now switches between the dynamic ranges [-1, 1] and [0, 1]. Because the range can change, the property's docstring should stay general and avoid details such as the active admissible value range. Here the property was named `voltage`, the adjustable parameter was `values`, and `self.voltage_values` supplied the chosen range.

### Instruments with similar features

For instruments that share many features, inherit common behavior from a parent instrument class instead of duplicating code.

Note

Remember to adjust the instrument's `name` attribute: pass the right argument to `super().__init__()` when that option exists, or set the attribute again after the call.

Sometimes a derived instrument only adds new properties or methods. Other times, existing properties or methods must be fully redefined in the subclass. When only selected details differ, dynamic properties provide a concise solution.

### Instrument family with different parameter values

A frequent pattern is an instrument family where each model shares the same interface but has different parameter ranges. In that case, update the class-specific range parameter without rewriting the property:

```python
class FictionalInstrumentFamily(Instrument):
    frequency = Instrument.setting(
        "FREQ %g",
        """Set the frequency (float).""",
        validator=strict_range,
        values=[0, 1e9],
        dynamic=True,
        # ... other possible parameters follow
    )

    # ... complete class implementation here

class FictionalInstrument_1GHz(FictionalInstrumentFamily):
    pass

class FictionalInstrument_3GHz(FictionalInstrumentFamily):
    frequency_values = [0, 3e9]

class FictionalInstrument_9GHz(FictionalInstrumentFamily):
    frequency_values = [0, 9e9]

```

This makes each family member easy to derive from the shared class, with the adjusted attribute defined on the class rather than on each instance.

### Instruments with similar command syntax

Dynamic properties can also preserve compatibility across instruments whose command syntax differs, as in this example.

```python
class MultimeterA(Instrument):
    voltage = Instrument.measurement(get_command="VOLT?",...)

    # ...full class definition code here

class MultimeterB(MultimeterA):
    # Same as brand A multimeter, but the command to read voltage
    # is slightly different
    voltage_get_command = "VOLTAGE?"

```

In this example, `MultimeterA` and `MultimeterB` use different voltage-read commands while all other behavior stays the same. Define `MultimeterB` by subclassing `MultimeterA` and implementing only that difference.
