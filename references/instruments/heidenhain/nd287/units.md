# pymeasure.instruments.heidenhain.ND287.units

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *units

Set or query the unit of measure recorded for the device. Valid values are ‘mm’ and ‘inch’. This parameter can only be changed manually on the device, so the property only checks that the instance units match the physical device configuration. I.e., it does not alter any physical device setting.
