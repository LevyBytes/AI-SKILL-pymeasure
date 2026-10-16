# pymeasure.instruments.velleman.VellemanK8090.write

[Owning PyMeasure class, adapter and connection contract](overview.md)

write(*command*, ***kwargs*)

Write command tailored to the K8090 protocol.

Overrides the corresponding method from the `Instrument` class.

Every packet sent to the device contains 7 bytes:

STX (0x04) - CMD - MASK - PARAM1 - PARAM2 - CHK - ETX (0x0F)

CHK is the package checksum.

Parameters:

**command** (*str*) - String such as "CMD[, MASK, PARAM1, PARAM2]"; only CMD is required.
