# pymeasure.instruments.hp.hp856Xx.HP856Xx.trace_data_format

HP856Xx.trace_data_format

Select the format used when trace data is transferred into or out of the instrument; see the TRA/TRB command. When reading data from the spectrum analyzer to a computer, the desired format must be specified. When sending data to the analyzer, specifying it is optional.

Type: `str` or `TraceDataFormat`

Warning

Use this only for manual trace-data readout. Avoid it unless the low-level trace format behavior is understood.
