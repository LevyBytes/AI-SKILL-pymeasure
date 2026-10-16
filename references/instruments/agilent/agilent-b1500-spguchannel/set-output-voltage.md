# pymeasure.instruments.agilent.agilentB1500.SPGUChannel.set_output_voltage

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_output_voltage(*source=1*, *base_voltage=0*, *peak_voltage=0*)

Configure the SPGU channel output voltage. (`SPV`)

Parameters:

- **source** (*SPGUSignalSource** or **int*) – Output-voltage signal source, defaults to `SPGUSignalSource.PULSE_SIGNAL_1`

- **base_voltage** (*float*) – Pulse base voltage or DC output voltage in V; defaults to 0

- **peak_voltage** (*float*) – Pulse peak voltage in V; defaults to 0
