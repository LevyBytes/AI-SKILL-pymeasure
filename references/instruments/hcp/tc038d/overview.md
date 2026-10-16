# pymeasure.instruments.hcp.TC038D

*class *pymeasure.instruments.hcp.TC038D(*adapter*, *name='TC038D'*, *address=1*, *timeout=1000*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Communication support for the HCP TC038D oven.

This newer version uses DC heating.

The oven expects raw bytes to be written, not ascii code, and it also sends raw bytes. Variables can use two or four-byte modes. The driver uses the four-byte mode addresses, where element count must be double the variables read.
