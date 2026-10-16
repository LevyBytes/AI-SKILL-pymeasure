# pymeasure.instruments.siglenttechnologies.siglent_sds1000xhd.MeasureChannel.simple_item

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *simple_item*: Any*

Set the simple measurement item.

This command configures a simple measurement type and whether it is active. Pass a tuple of (item, state).
For item (str), choose the measurement item to configure.
Valid item values include PKPK, MAX, MIN, AMPL, TOP, BASE, LEVELX, CMEAN, MEAN, and STDEV.
More item values include VSTD, RMS, CRMS, MEDIAN, CMEDIAN, OVSN, FPRE, OVSP, RPRE, and PER.
Timing item values include FREQ, TMAX, TMIN, PWID, NWID, DUTY, NDUTY, WID, NBWID, and DELAY.
Edge and area item values include TIMEL, RISE, FALL, RISE20T80, FALL80T20, CCJ, PAREA, NAREA, AREA, and ABSAREA.
Pulse and accumulated-area item values include CYCLES, REDGES, FEDGES, EDGES, PPULSES, NPULSES, PACArea, NACArea, ACArea, and ABSACArea.
For state (str), use the measurement-item state ON or OFF.
