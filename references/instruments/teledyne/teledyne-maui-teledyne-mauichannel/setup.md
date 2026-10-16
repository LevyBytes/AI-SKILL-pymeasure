# pymeasure.instruments.teledyne.teledyneMAUI.TeledyneMAUIChannel.setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

setup(***kwargs*)

Configure the channel, leaving unspecified settings unchanged.

Changing values such as probe attenuation can also change offset, range, and related settings. Check the oscilloscope documentation and call setup() multiple times if staged updates are needed. Property descriptions provide additional detail.

Parameters:

- **bwlimit**

- **coupling**

- **display**

- **offset**

- **probe_attenuation**

- **scale**

- **trigger_coupling**

- **trigger_level**

- **trigger_slope**
