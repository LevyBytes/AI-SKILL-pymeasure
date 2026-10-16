# pymeasure.instruments.oxfordinstruments.IPS120_10.switch_heater_enabled

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *switch_heater_enabled

Boolean control/readback indicating switch-heater enablement. For `True`, magnet-current control is possible; the stated switch condition is both closed and open. For `False`, the switch is closed and magnet current cannot be controlled.

When setting the switch heater to `True`, activation occurs only if the power-supply current matches the magnet's last recorded current.

Warning

Using `"Force"` instead of `True` omits these checks. Caution: skipping them can seriously damage both the power supply and the magnet.

After the switch heater is turned on, wait several seconds for the switch to respond.

Raises `SwitchHeaterError` if, when status is read, the system reports a 'heater fault' or reports that no switch is fitted.
