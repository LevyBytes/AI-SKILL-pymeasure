# pymeasure.instruments.hp.hp856Xx.HP856Xx.marker_signal_tracking_enabled

HP856Xx.marker_signal_tracking_enabled

Control whether center frequency tracks the active marker.

After each sweep, the analyzer recenters using the marker value as the center frequency. This makes it possible to move quickly from a wide span to a narrow span without losing the signal from the screen. Alternatively, use ‘marker_signal_tracking_enabled’ to keep a slowly drifting signal centered. When enabled, a “K” appears at the left edge of the display.

Type: `bool`
