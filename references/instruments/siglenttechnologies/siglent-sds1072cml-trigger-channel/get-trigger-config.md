# pymeasure.instruments.siglenttechnologies.siglent_sds1072cml.TriggerChannel.get_trigger_config

[Owning PyMeasure class, adapter and connection contract](overview.md)

get_trigger_config()

Return the active trigger configuration as a dict with these keys: - “type”: waveform acquisition condition [EDGE, slew,GLIT,intv,runt,drop] - “source”: source for trigger (str, {EX,EX/5,C1,C2}) - “hold_type”: hold category (refer to page 131 of programing guide) - “hold_value1”: hold value1 setting (refer to page 131 of programing guide) - “level”: trigger set Level (float) - “slope”: (str,{POS,NEG,WINDOW}) Trigger on rising, falling or Window. - “mode”: post-trigger behavior (str, {NORM, AUTO, SINGLE,STOP}) - “coupling”: trigger-channel coupling (str,{AC,DC})

and refreshes the internal configuration status
