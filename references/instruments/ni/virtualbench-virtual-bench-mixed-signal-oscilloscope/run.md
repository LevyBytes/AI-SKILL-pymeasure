# pymeasure.instruments.ni.virtualbench.VirtualBench.MixedSignalOscilloscope.run

[Owning MixedSignalOscilloscope contract](overview.md)

run(*autoTrigger=True*)

Moves acquisition from Stopped state to Running state. If it is currently Triggered, acquisition first moves to Stopped state, then to Running state. The method returns an error when excessive power is present on any enabled channel.

Parameters:

**autoTrigger** (*bool*) – Enable/Disable auto triggering
