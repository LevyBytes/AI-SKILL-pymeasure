# pymeasure.instruments.siglenttechnologies.siglent_sds1072cml.TriggerChannel.trigger_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger_setup*: Any*

Return the active trigger setup as a dict with keys: - “type”: waveform acquisition condition [EDGE, slew,GLIT,intv,runt,drop] - “source”: source for trigger (str, {EX,EX/5,C1,C2}) - “hold_type”: hold category (refer to page 131 of programing guide) - “hold_value1”: hold value1 setting (refer to page 131 of programing guide)
