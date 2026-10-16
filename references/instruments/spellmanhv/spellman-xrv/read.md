# pymeasure.instruments.spellmanhv.SpellmanXRV.read

[Owning PyMeasure class, adapter and connection contract](overview.md)

read()

Read a response from the device, then validate it for errors.

Raise:

ConnectionError if the response lacks an initial &lt;STX&gt; or has a bad checksum. TCPIP connections skip checksum validation.

Return type:

`str`
