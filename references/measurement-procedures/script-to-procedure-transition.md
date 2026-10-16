# Script measurement limitations and Procedure transition

[Keithley 2400 scripted IV measurement workflow](keithley2400-iv-workflow.md) / [Complete Keithley 2400 IV measurement script](keithley2400-iv-script.md)

When run, this example script performs the measurement and writes the data to a CSV file. That can be enough for simple work, but it also exposes several problems that PyMeasure is designed to address. In the plain-script version, the main drawbacks are:

- Measurement progress is difficult to observe

- Saved data does not carry its input-parameter context

- The run does not display a live plot, and this example does not plot afterward either

- Data is written only after a clean finish, so interrupted runs lose the output

- Canceling an active measurement can leave the system state undefined

- Exceptions can likewise leave the system state undefined

The [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) class addresses these limitations. The following section introduces the [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) class and adapts the script example so it can use that interface and its supporting features.
