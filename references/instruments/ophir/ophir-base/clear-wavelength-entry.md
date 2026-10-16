# pymeasure.instruments.ophir.ophir_base.OphirBase.clear_wavelength_entry

[Owning PyMeasure class, adapter and connection contract](overview.md)

clear_wavelength_entry(*index*)

Remove the wavelength-list entry at the given zero-based index.

The entry cannot be the active index. Use `define_wavelength_entry()` to assign a new value. Read `wavelength_list` for the configured entries and wavelength limits.

Return type:

`None`
