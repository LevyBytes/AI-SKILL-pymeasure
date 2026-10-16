# pymeasure.instruments.teledyne.TeledyneMAUI.hardcopy_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

hardcopy_setup(***kwargs*)

Specify hardcopy settings.

Configure a printer connection or file-save behavior. Any subset of these parameters may be set.

Parameters:

- **device** – {BMP, JPEG, PNG, TIFF}

- **format** – {PORTRAIT, LANDSCAPE}

- **background** – {Std, Print, BW}

- **destination** – {PRINTER, CLIPBOARD, EMAIL, FILE, REMOTE}

- **area** – {GRIDAREAONLY, DSOWINDOW, FULLSCREEN}

- **directory** – Legal DOS path, only for FILE mode

- **filename** – Filename string without extension, only for FILE mode

- **printername** – Valid printer name, only for PRINTER mode

- **portname** – {GPIB, NET}
