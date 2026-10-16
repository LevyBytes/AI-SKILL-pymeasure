# pymeasure.instruments.velleman.VellemanK8090.switch_on

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *switch_on*: Any*

Switch channels to the on state without affecting other channels. Provide a list or set of channel numbers, beginning at 1, or provide a bitmask.

Once switching is requested, this waits for the device reply. The reply is sent only when a relay toggles, so otherwise the call can block for the communication timeout. Avoid unnecessary switch_ calls when speed matters.
