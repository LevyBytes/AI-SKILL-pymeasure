# pymeasure.instruments.temptronic.ATSBase.wait_for_settling

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_settling(*time_limit=300*)

block script execution until TS reports settled.

Parameters:

**time_limit** — maximum blocking time allowed for TS to settle (float). (default: `300`)

Returns:

self

Script execution remains blocked until TS settles or time_limit is exceeded (float).
