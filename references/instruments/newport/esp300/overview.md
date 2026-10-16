# pymeasure.instruments.newport.ESP300

*class *pymeasure.instruments.newport.ESP300(*adapter*, *name='Newport ESP 300 Motion Controller'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model for the Newport ESP 300 Motion Controller, providing a high-level interface to the instrument.

By default, construction creates x, y, and phi attributes for axes 1, 2, and 3. Custom implementations may override this for the axes they expose. Axes are managed through an `Axis` class.

## Related property contracts

- Open when checking pymeasure.instruments.newport.ESP300.axes: [axes](axes.md).
