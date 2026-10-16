# pymeasure.instruments.agilent.agilentE5062A.VNAChannel.attenuation

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *attenuation

Set or read stimulus attenuation in dB (positive int), from 0 to 40 in increments of 10. Default is 0 dB. Allowed stimulus power occupies a 15 dB span: (`attenuation` - 5 dB, `attenuation` + 10 dB).

Requires the power range extension; without that extension installed, the command is ignored.
