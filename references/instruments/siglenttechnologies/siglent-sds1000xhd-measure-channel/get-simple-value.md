# pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.MeasureChannel.get_simple_value

[Owning PyMeasure class, adapter and connection contract](overview.md)

get_simple_value(*measurement_type*)

Return the value for a selected simple measurement type.

This method reads the current value for the requested simple measurement type.

Parameters:

**measurement_type** (*str*) –

Measurement type to query.
Valid values include PKPK, MAX, MIN, AMPL, TOP, BASE, LEVELX, CMEAN, MEAN, and STDEV.
Additional values include VSTD, RMS, CRMS, MEDIAN, CMEDIAN, OVSN, FPRE, OVSP, RPRE, and PER.
Timing-related values include FREQ, TMAX, TMIN, PWID, NWID, DUTY, NDUTY, WID, NBWID, and DELAY.
Edge and area values include TIMEL, RISE, FALL, RISE20T80, FALL80T20, CCJ, PAREA, NAREA, AREA, and ABSAREA.
Pulse and accumulated-area values include CYCLES, REDGES, FEDGES, EDGES, PPULSES, NPULSES, PACArea, NACArea, ACArea, and ABSACArea.

Note: use the simple_value_all property to retrieve every measurement value in one call.

Returns:

Measurement value returned in NR3 format (e.g., 1.23E+2)

Return type:

float
