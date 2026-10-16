# pymeasure.instruments.siglenttechnologies.siglent_sds1072cml.TriggerChannel.set_trigger_config

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_trigger_config(***kwargs*)

Apply the active trigger configuration using these keys: - “type”: waveform acquisition condition [EDGE, slew,GLIT,intv,runt,drop] - “source”: source for trigger (str, {EX,EX/5,C1,C2}) - “hold_type”: hold category (refer to page 131 of programing guide) - “hold_value1”: hold value1 setting (refer to page 131 of programing guide) - “level”: trigger set Level (float) - “slope”: (str,{POS,NEG,WINDOW}) Trigger on rising, falling or Window. - “mode”: post-trigger behavior (str, {NORM, AUTO, SINGLE,STOP}) - “coupling”: trigger-channel coupling (str,{AC,DC})

Return a flag showing whether every specified entry was set correctly on the oscilloscope, and refresh the internal trigger configuration.
