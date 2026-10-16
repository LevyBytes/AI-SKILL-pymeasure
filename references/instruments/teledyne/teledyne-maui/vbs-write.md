# pymeasure.instruments.teledyne.TeledyneMAUI.vbs_write

[Owning PyMeasure class, adapter and connection contract](overview.md)

vbs_write(*message*)

Send a VBS command straight to the device.

This oscilloscope class also permits direct Visual Basic Scripting (VBScript) use. The method sends a literal VBS command. Use the ‘MAUI Browser’ on the oscilloscope to inspect all available variables.

Minimal usage example:

```python
instrument.vbs_write("app.Display.GridMode = Dual")

```
