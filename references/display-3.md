# Thread, Qt, Listeners, Inputs

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Thread classes; Qt classes; Listeners classes; Inputs classes.

## Thread classes

### Thread classes

 *class *pymeasure.display.thread.StoppableQThread(*parent=None*)

Bases: `QThread`

Base class for QThreads that must support stopping through a thread-safe method call.

 join(*timeout=0*)

Join the current thread; if needed, force it to stop once the timeout has elapsed.

Parameters:

**timeout** - Duration of the timeout in seconds (default: `0`).

## Qt classes

### Qt classes

Import Qt through `pymeasure.display.Qt` so the same import path works for PySide and PyQt4.

 Qt.fromUi(***kwargs*)

Return a Qt object built from its arguments with loadUiType. The returned object also receives every QWidget object from the form class for convenient access.

## Listeners classes

### Listeners classes

 *class *pymeasure.display.listeners.Monitor(*queue*)

Bases: `QThread`

Monitor uses a queue to receive status and progress messages from a Worker, preventing message loss.

 run(*self*)

 *class *pymeasure.display.listeners.QListener(*port*, *topic=''*, *timeout=0.01*)

Bases: [`StoppableQThread`](https://pymeasure.readthedocs.io/en/latest/api/display/thread.html#pymeasure.display.thread.StoppableQThread)

Base class for QThreads that listen for messages on a ZMQ TCP port and support stopping through a thread- and process-safe method call.

## Inputs classes

### Inputs classes

 *class *pymeasure.display.inputs.BooleanInput(*parameter*, *parent=None*, ***kwargs*)

Bases: `Input`, `QCheckBox`

Checkbox input for boolean values that is connected to a `BooleanParameter`.

 set_parameter(*parameter*)

Attach a new parameter to the input box and initialize the box's value.

Parameters:

**parameter** – parameter to connect.

 *class *pymeasure.display.inputs.Input(*parameter*, ***kwargs*)

Bases: `object`

Mix-in class for connecting a [`Parameter`](https://pymeasure.readthedocs.io/en/latest/api/experiment/parameters.html#module-pymeasure.experiment.parameters) object with a GUI input box.

Parameters:

**parameter** - Parameter instance that should be connected to this input box.

Attr parameter:

Read-only property for retrieving the associated parameter.

 *property *parameter

The parameter object currently connected. This property is read-only; see `set_parameter()`.

Reading this property also updates its value from the GUI input box as a side effect.

 set_parameter(*parameter*)

Attach a new parameter to the input box and initialize the box's value.

Parameters:

**parameter** – parameter to connect.

 update_parameter()

Set the parameter value from the current value held by the Input GUI element.

 *class *pymeasure.display.inputs.IntegerInput(*parameter*, *parent=None*, ***kwargs*)

Bases: `Input`, `QSpinBox`

Spin input box for integer values that is connected to a `IntegerParameter`.

 set_parameter(*parameter*)

Attach a new parameter to the input box and initialize the box's value.

Parameters:

**parameter** – parameter to connect.

 stepEnabled(*self*) → QAbstractSpinBox.StepEnabledFlag

 *class *pymeasure.display.inputs.ListInput(*parameter*, *parent=None*, ***kwargs*)

Bases: `Input`, `QComboBox`

Dropdown input for list values that is connected to a `ListParameter`.

 set_parameter(*parameter*)

Attach a new parameter to the input box and initialize the box's value.

Parameters:

**parameter** – parameter to connect.

 *class *pymeasure.display.inputs.ScientificInput(*parameter*, *parent=None*, ***kwargs*)

Bases: `Input`, `QDoubleSpinBox`

Spinner input box for floating-point values connected to a `FloatParameter`. When appropriate, this box displays and accepts values written in scientific notation.

See also

Class `FloatInput`

Used for a floating-point input box without scientific notation.

 set_parameter(*parameter*)

Attach a new parameter to the input box and initialize the box's value.

Parameters:

**parameter** – parameter to connect.

 stepEnabled(*self*) → QAbstractSpinBox.StepEnabledFlag

 textFromValue(*self*, *v: float*) → str

 validate(*self*, *input: str | None*, *pos: int*)

 valueFromText(*self*, *text: str | None*) → float

 *class *pymeasure.display.inputs.StringInput(*parameter*, *parent=None*, ***kwargs*)

Bases: `Input`, `QLineEdit`

String input box connected to a `Parameter`. Parameter subclasses based on strings may use this input as well; non-string parameters should be handled by more specialised input classes.

 *class *pymeasure.display.inputs.VectorInput(*parameter*, *parent=None*, ***kwargs*)

Bases: `StringInput`

String input box connected to a `VectorParameter`. The box displays and accepts lists.
