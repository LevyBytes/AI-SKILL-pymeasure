# pymeasure.instruments.lecroy.LeCroyT3DSO1204.default_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

default_setup()

Prepare the oscilloscope for remote operation.

For remote operation, force COMM_HEADER to OFF. COMM_HEADER determines how query responses are formatted, but it does not change how the oscilloscope parses inbound messages. Long and short headers may be sent regardless of CHDR. With COMM_HEADER set to OFF, replies contain minimal information and are easier for the driver to parse. During normal operation, do not change COMM_HEADER; any setting other than OFF causes this driver to fail.
