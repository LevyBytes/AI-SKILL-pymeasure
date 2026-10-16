# pymeasure.instruments.thyracont.smartline_v2.SmartlineV2

Covers: Smartline V2 Transmitter Series; Thyracont; Smartline V1 Transmitter Series; ILX Lighwave LDP3811; ILX Lightwave; Racal-Dana 1992 Universal Counter; Racal-Dana.

## Smartline V2 Transmitter Series

### Smartline V2 Transmitter Series

 *class *pymeasure.instruments.thyracont.smartline_v2.SmartlineV2(*adapter*, *name='Thyracont SmartlineV2 Transmitter'*, *baud_rate=115200*, *address=1*, *timeout=250*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

A Smartline V2 series Thyracont transmitter for vacuum sensor measurements.

Subclass this Instrument and add the needed channels; the example below shows the pattern.

```pycon
from pymeasure.instruments import Instrument
from pymeasure.instruments.thyractont import SmartlineV2

PiezoAndPiraniInstrument(SmartlineV2):
    piezo = Instrument.ChannelCreator(Piezo)
    pirani = Instrument.ChannelCreator(Pirani)

```

Communication Protocol v2 via RS485:

- Communication payloads use ASCII characters throughout.

- Package (bytes and usage):

  - 0-2 address, 3 access code, 4-5 command, 6-7 data length.

  - if data: 8-n contain payload data, n+1 checksum, n+2 carriage return

  - if no data: 8 contains checksum, 9 carriage return

- Access codes (request: master->transmitter, response: transmitter->master):

  - read: 0, 1

  - write: 2, 3

  - factory default: 4,5

  - error: -, 7

  - binary 8, 9

- Data length is the byte count of the data, left padded with zeroes

- Checksum: Sum the preceding characters as decimal numbers, apply mod 64, add 64, and emit the ASCII character.

Parameters:

**adress** – Device address, valid from 1-16.
