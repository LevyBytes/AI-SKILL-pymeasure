# pymeasure.instruments.spellmanhv.SpellmanXRV.checksum

[Owning PyMeasure class, adapter and connection contract](overview.md)

*static *checksum(*string_to_check*)

Calculate the checksum.

Parameters:

**string_to_check** (`str`) – source string used when calculating the checksum

Return type:

`str`

Use this procedure to compute the checksum:

- Before &lt;CSUM&gt;, sum every byte except &lt;STX&gt; into a 16 bit (or larger) word; treat each byte as an unsigned integer.

- Take the two’s complement.

- Keep only the eight least significant bits of the accumulated value.

- On the resulting byte, force the most significant bit (bit 7) to 0 by applying bitwise AND with 0x7F.

- Then force the next most significant bit (bit 6) to 1 using bitwise OR with 0x40.

With that algorithm, the checksum always falls from 0x40 through 0x7F. Because &lt;STX&gt; and &lt;ETX&gt; use ASCII values outside that range, the checksum cannot be mistaken for either control character.
