# pymeasure.instruments.ophir.ophir_base.OphirBase.define_wavelength_entry

[Owning PyMeasure class, adapter and connection contract](overview.md)

define_wavelength_entry(*index*, *value*)

Set a wavelength in nm at the given zero-based position in the wavelength list.

The target wavelength-list slot must be empty; clear it with `clear_wavelength_entry()`. Read `wavelength_list` for the configured entries and wavelength limits.

Return type:

`None`
