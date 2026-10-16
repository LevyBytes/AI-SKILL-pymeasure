# pymeasure.instruments.ni.virtualbench.VirtualBench

*class *pymeasure.instruments.ni.virtualbench.VirtualBench(*device_name=''*, *name='VirtualBench'*)

Bases: `object`

Represents National Instruments Virtual Bench main frame.

The module-specific behavior is supplied by subclasses:
- Mixed-Signal-Oscilloscope (MSO)

- Digital Input Output (DIO)

- Function Generator (FGEN)

- Power Supply (PS)

- Serial Peripheral Interface (SPI) -> not currently implemented in pymeasure

- Inter Integrated Circuit (I2C) -> not currently implemented in pymeasure

Each module has file-based save/load configuration methods. Those wrappers are not present yet; see the pyvirtualbench file for details.

Calibration classes and methods are not currently wrapped because they are rarely needed. Network connection support is also absent; consult the pyvirtualbench file when that capability is required.

Parameters:

- **device_name** (*str*) – Full unique device name

- **name** (*str*) — Display label used by pymeasure
