# pymeasure.instruments.teledyne.TeledyneOscilloscope.default_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

default_setup()

Prepare the oscilloscope for control from a remote client.

COMM_HEADER selects how query replies from the oscilloscope are formatted. It does not change how incoming messages are parsed by the instrument. Header mnemonics may still be sent in either long or short spelling regardless of CHDR. Setting COMM_HEADER to OFF makes replies contain only the essential data, which simplifies parsing. User code should leave COMM_HEADER alone during normal operation, because any value other than OFF prevents this driver from interpreting responses correctly.
