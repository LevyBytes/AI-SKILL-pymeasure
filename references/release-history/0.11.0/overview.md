# Version 0.11.0 (2022-11-19)

Primary highlights in this release:

- 11 new instrument drivers have been added

- Adds a way to test instrument communication **without** connected hardware; see the [protocol-tests documentation](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments.html#protocol-tests).

- Refines the split between `Instrument` and `Adapter` to simplify future changes. Adapters handle hardware communication, while the communication *protocol* belongs in Instruments. A later section gives the details.

- Makes the GUI work with Qt6.

- Begins API cleanup for a later version 1.0. Deprecated items and their eventual removals will be called out clearly in the changelog.
