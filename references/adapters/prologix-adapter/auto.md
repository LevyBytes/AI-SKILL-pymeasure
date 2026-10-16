# pymeasure.adapters.PrologixAdapter.auto

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *auto

Choose whether instruments are addressed to talk after a command is sent (bool).

Set the Prologix GPIB controller to address instruments to talk automatically after commands so responses can be read. The Read-After-Write feature removes the need for repeated read commands; this property turns it on with True or off with False.
