# pymeasure.instruments.spellmanhv.SpellmanXRV.write

[Owning PyMeasure class, adapter and connection contract](overview.md)

write(*command*)

Write to the instrument.

Before transmission, prefixes each command with &lt;STX&gt; (0x02) and appends checksum + &lt;ETX&gt; (0x03). TCPIP connections omit the checksum.

Return type:

`None`
