# pymeasure.instruments.activetechnologies.AWG401x_AWG.run_mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *run_mode*: Any*

Set or query the AWG run mode. The possible values are:

- CONT&lt;INUOUS&gt;: waveforms repeat according to the entry repetition parameter, and the full sequence loops circularly.

- BURS&lt;T&gt;: the AWG waits for a trigger event. After that trigger, each waveform repeats according to the entry repetition parameter, and the full sequence loops circularly for the number of cycles specified by Burst Count[N]. With Burst Count[N]=1, the instrument enters Single mode and runs the sequence one time.

- TCON&lt;TINUOUS&gt;: the AWG waits for a trigger event, then repeats each waveform according to the entry repetition parameter while the full sequence loops circularly.

- STEP&lt;PED&gt;: before executing each sequencer entry, the AWG waits for a trigger event. The entry waveform repeats according to the entry repetition parameter. After an entry finishes generating, the output holds either that entry final sample or the upcoming entry initial sample until another trigger arrives. When the sequence reaches its end, execution starts again at the first entry.

- ADVA&lt;NCED&gt;: enables the “Advanced” mode. In this mode, sequence execution may be redirected with conditional and unconditional jumps (JUMPTO and GOTO commands) plus dynamic jumps (PATTERN JUMP commands).

The *RST command restores this parameter to CONTinuous.
