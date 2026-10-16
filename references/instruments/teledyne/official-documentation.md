# instruments — teledyne documentation links

- [Teledyne](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/index.html)
- [Teledyne T3AFG Arbitrary Waveform Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyneT3AFG.html)
- [Teledyne Oscilloscope base classes](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html)

Covers: Teledyne; Teledyne T3AFG Arbitrary Waveform Generator.

## Teledyne

### Teledyne

Find Teledyne-specific notes here for the instruments currently implemented. For an instrument missing from this list, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

When the instrument you need is absent here, older models may appear under [LeCroy](https://pymeasure.readthedocs.io/en/latest/api/instruments/lecroy/index.html).


Teledyne oscilloscopes share base classes. Some devices can use those classes directly; the confirmed devices are:
- [`TeledyneMAUI`](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html#pymeasure.instruments.teledyne.TeledyneMAUI)

  - Teledyne LeCroy HDO6xxx series (e.g. HDO6054B)

A device absent from the list may still work adequately with the base class. When adding another device, these base classes reduce the new code required.
- [Teledyne Oscilloscope](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html#teledyne-oscilloscope)
- [Teledyne Channel](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html#teledyne-channel)
- [Teledyne MAUI Oscilloscope](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html#teledyne-maui-oscilloscope)
- [Teledyne MAUI Channel](https://pymeasure.readthedocs.io/en/latest/api/instruments/teledyne/teledyne_bases.html#teledyne-maui-channel)
