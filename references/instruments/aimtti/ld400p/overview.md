# pymeasure.instruments.aimtti.ld400p.LD400P

Covers: Aim-TTi Electronic Loads; Aim-TTI; Aim-TTI PL Series Power Supplies; MKS Instruments Abstract Instrument; MKS Instruments 937B Vacuum Gauge Controller; MKS Instruments; MKS Instruments 974B Vacuum Pressure Transducer; Danfysik; Danfysik 8500 Power Supply; Resource Manager.

## Aim-TTi Electronic Loads

### Aim-TTi Electronic Loads

 *class *pymeasure.instruments.aimtti.ld400p.LD400P(*adapter*, *name='LD400'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Aim-TTi LD400P electronic DC load interface.

Note: digital communication is available on the LD400P only; the LD400 edition has no digital interface.

The LD400[P] [manual](https://resources.aimtti.com/manuals/LD400+LD400P_Instruction_Manual_EN_48511-1730_8.pdf) documents this interface.

Although `SCPIMixin` is inherited, this device does not handle the command options, `next_error`, or `check_errors` features.
