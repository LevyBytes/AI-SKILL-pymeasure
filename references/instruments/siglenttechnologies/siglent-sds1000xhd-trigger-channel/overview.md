# pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.TriggerChannel

*class *pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.TriggerChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

SDS1000xHD oscilloscope trigger channel.

This class exposes full SDS1000xHD trigger control through SCPI commands. It manages trigger-type-specific settings, because trigger types such as EDGE, SLOPe, etc. keep separate source, level, and coupling values. Supported source parameter values are: C1, C2, C3, C4, EX, EX5, LINE, where: - C1-C4: inputs from channels - EX: the external trigger input - EX5: the external trigger input divided by 5 - LINE: trigger from line frequency
