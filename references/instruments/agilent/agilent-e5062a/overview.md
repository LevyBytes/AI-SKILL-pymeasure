# pymeasure.instruments.agilent.AgilentE5062A

Class constructor: pymeasure.instruments.agilent.AgilentE5062A(adapter, **kwargs).
Default name: 'Agilent E5062A Vector Network Analyzer'.

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Agilent E5062A Vector Network Analyzer

This VNA provides 4 independent channels, and every channel owns its sweep. They are exposed through the `channels` dictionary. A channel may be enabled without being shown. Many operations tied to a trace, including data reads, are performed through the channel but apply only to the *active trace*.

A channel can show as many as 4 traces, set by `visible_traces`. Each channel also exposes `display_layout`, which determines trace arrangement within that channel. Trace objects live in the `traces` dictionary, for example `vna.channels[1].traces[1]`.

The VNA has several transfer formats, but this API works only with IEEE 64-bit floating point format. Initialization configures the VNA to use that format, and data transfer format is not exposed as a public property.

Only part of the full E5062A feature set is implemented here. Notable missing pieces include (TODO):

- changing the display scale

- markers

- calibration

- power sweeps

```python
from pymeasure.instruments.agilent.agilentE5062A import AgilentE5062A

# connect to the VNA and make a measurement consisting of 10 averages
vna = AgilentE5062A("TCPIP::192.168.2.233::INSTR")
ch = vna.channels[1]            # use channel 1
ch.visible_traces = 4            # use all 4 traces
for i, (tr, parameter) in enumerate(zip(
        ch.traces.values(),
        ['S11', 'S12', 'S21', 'S22'])):
    tr.parameter = parameter

ch.averages = 10                # use 10x averaging
ch.averaging_enabled = True     # turn averaging on
ch.trigger_continuous = False   # turn off continuous triggering
vna.trigger_source = 'BUS'      # require remote trigger
vna.abort()                     # stop the current sweep
ch.restart_averaging()          # clear current averaging
for _ in range(ch.averages):
    ch.trigger_initiate()       # arm channel 1 for single sweep
    vna.trigger_single()        # send a trigger
    vna.wait_for_complete()     # wait until the sweep is complete

# see `agilentE5062A.data` for an example of saving the measurement

```
