# pymeasure.instruments.ophir.ophir_base.OphirBase

*class *pymeasure.instruments.ophir.ophir_base.OphirBase(*adapter*, *name='Ophir'*, ***kwargs*)

Bases: `OphirCommunication`

Represents an Ophir laser power/energy meter device.

The shared command set applies to USBI, Juno, Juno+, NovaII, Vega, StarLite, StarBright, and Centauri devices. Some of those devices support additional commands exposed through Mixin classes. Other devices, including Nova and Pulsar, implement only a subclass of this command group.
