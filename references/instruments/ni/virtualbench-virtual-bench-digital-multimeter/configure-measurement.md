# pymeasure.instruments.ni.virtualbench.VirtualBench.DigitalMultimeter.configure_measurement

[Owning DigitalMultimeter contract](overview.md)

configure_measurement(*dmm_function*, *auto_range=True*, *manual_range=1.0*)

Set up the Instrument for a DMM measurement

Parameters:

- **name** (*dmm_function:DMM function index or*) ?
  - `'DC_VOLTS'`, `'AC_VOLTS'`

  - `'DC_CURRENT'`, `'AC_CURRENT'`

  - `'RESISTANCE'`

  - `'DIODE'`

- **auto_range** (*bool*) – Enable/Disable auto ranging

- **manual_range** (*float*) – Manually set measurement range
