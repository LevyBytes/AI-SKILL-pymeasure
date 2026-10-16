# pymeasure.instruments.kuhneelectronic.Kusg245_250A.store_settings

[Owning PyMeasure class, adapter and connection contract](overview.md)

store_settings()

Save actual settings to EEPROM.

Stored settings include the fine-frequency mode flag (`freq_steps_fine_enabled`), the active frequency value (`frequency_coarse` or `frequency_fine`), and the output power target (`power_setpoint`). They also include external ON/OFF control (`external_enabled`), reflection limiting (`reflection_limit`), pulse on time (`pulse_width`), and pulse off time (`off_time`).
