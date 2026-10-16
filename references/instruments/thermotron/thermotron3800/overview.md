# pymeasure.instruments.thermotron.Thermotron3800

Covers: Thermotron 3800 Oven; Thermotron; Delta Elektronica SM7045D Power source; Delta Elektronika; PTW Freiburg; PTW UNIDOS Tango/Romeo dosemeters; PTW DIAMENTOR DAP dosemeters; Anapico; Anapico APSIN12G Signal Generator; FormFactor; FormFactor Velox Wafer Prober.

## Thermotron 3800 Oven

### Thermotron 3800 Oven

 *class *pymeasure.instruments.thermotron.Thermotron3800(*adapter*, *name='Thermotron 3800'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Thermotron 3800 Oven. This driver currently addresses only Control Channel 1, and each write command is followed by a built-in 1000ms delay.
