# pymeasure.instruments.ni.virtualbench.VirtualBench.DigitalInputOutput.read

[Owning DigitalInputOutput contract](overview.md)

read(*lines*)

Gets the present state for the requested lines.

Parameters:

**lines** (*str*) — Line string; use the complete name such as `'VB8012-xxxxxxx/dig/0:7'` because instrument_handle is not required (only library_handle)

Returns:

Line state list (HIGH/LOW)

Return type:

list
