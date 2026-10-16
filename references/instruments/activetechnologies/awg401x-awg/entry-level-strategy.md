# pymeasure.instruments.activetechnologies.AWG401x_AWG.entry_level_strategy

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *entry_level_strategy*: Any*

Set or query the Entry Length Strategy. This setting determines how sequencer entry lengths relate to the channel waveform lengths assigned to each entry. The possible values are:

- ADAPTL&lt;ONGER&gt;: by default, a sequencer entry uses the length of the longest analog-channel waveform assigned to that entry.

- ADAPTS&lt;HORTER&gt;: by default, a sequencer entry uses the length of the shortest analog-channel waveform assigned to that entry.

- DEF&lt;AULT&gt;: by default, a sequencer entry uses the value configured by the Sequencer Item Default Length [N] parameter
