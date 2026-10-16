# pymeasure.instruments.agilent.agilentB1500.SPGUChannel.apply_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

apply_setup()

Send the present configuration to the SPGU channel. (`SPUPD`)

Behavior follows `SPGU.operation_mode` (`SIM`):

- PG mode: base output voltage comes from `SPV`

- ALWG mode: output starts from the waveform initial value
