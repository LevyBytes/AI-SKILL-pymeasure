# Tektronix, Rigol

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: TDS2000 Oscilloscope; Tektronix; AFG3152C Arbitrary function generator; Rigol DG800 waveform generator; Rigol.

## TDS2000 Oscilloscope

### TDS2000 Oscilloscope

 *class *pymeasure.instruments.tektronix.TDS2000(*adapter*, *name='Tektronix TDS 2000 Oscilloscope'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Tektronix TDS 2000 Oscilloscope and exposes a high-level interface for using the instrument.

## Tektronix

### Tektronix

This section documents the implemented Tektronix instruments. For an instrument that is absent, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [TDS2000 Oscilloscope](https://pymeasure.readthedocs.io/en/latest/api/instruments/tektronix/tds2000.html)
  - [`TDS2000`](https://pymeasure.readthedocs.io/en/latest/api/instruments/tektronix/tds2000.html#pymeasure.instruments.tektronix.TDS2000)

- [AFG3152C Arbitrary function generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/tektronix/afg3152c.html)
  - [`AFG3152C`](https://pymeasure.readthedocs.io/en/latest/api/instruments/tektronix/afg3152c.html#pymeasure.instruments.tektronix.AFG3152C)
  - [`AFG3152CChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/tektronix/afg3152c.html#pymeasure.instruments.tektronix.afg3152c.AFG3152CChannel)

## AFG3152C Arbitrary function generator

### AFG3152C Arbitrary function generator

 *class *pymeasure.instruments.tektronix.AFG3152C(*adapter*, *name='Tektronix AFG3152C arbitrary function generator'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the Tektronix AFG 3000 series arbitrary function generator, with one or two channels, and exposes a high-level interface for operating the instrument.

```python
afg=AFG3152C("GPIB::1")        # AFG on GPIB 1
afg.reset()                    # Reset to default
afg.ch1.shape='sinusoidal'     # Sinusoidal shape
afg.ch1.unit='VPP'             # Sets CH1 unit to VPP
afg.ch1.amp_vpp=1              # Sets the CH1 level to 1 VPP
afg.ch1.frequency=1e3          # Sets the CH1 frequency to 1KHz
afg.ch1.enable()               # Enables the output from CH1

```

 *class *pymeasure.instruments.tektronix.afg3152c.AFG3152CChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

 *property *amp_dbm*: Any*

Adjust the output amplitude expressed in dBm. (float)

 *property *amp_vpp*: Any*

Adjust the output amplitude expressed in Vpp. (float)

 *property *amp_vrms*: Any*

Adjust the output amplitude expressed in Vrms. (float)

 *property *duty*: Any*

Adjust the pulse duty cycle. (float))

 *property *frequency*: Any*

Control the frequency. (float)

 *property *impedance*: Any*

Set the channel output impedance. Use caution with this setting.

 insert_id(*command*)

Add the channel id before most write operations.

 *property *offset*: Any*

Set the amplitude offset, always using Volt as the unit. (float)

 *property *shape*: Any*

Set the output shape. (str)

 *property *unit*: Any*

Control the amplitude unit. (str)

 waveform(*shape='SIN'*, *frequency=1000000.0*, *units='VPP'*, *amplitude=1*, *offset=0*)

General-purpose setting routine for a full wavefunction.

Return type:

`None`

## Rigol DG800 waveform generator

### Rigol DG800 waveform generator

 *class *pymeasure.instruments.rigol.DG800(*adapter*, *name='DG800'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models a Rigol DG800-series waveform generator and exposes a high-level interface for operating the instrument.

 channel_1

Channel:

`VoltageChannel`

 channel_2

Channel:

`VoltageChannel`

 *class *pymeasure.instruments.rigol.rigol_dg800.VoltageChannel(*parent*, *id*, ***kwargs*)

Bases: [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)

Models one signal-generator channel.

 *property *dc*: Any*

Configure the waveform generator to produce a DC voltage in V.

 *property *duty_cycle*: Any*

Adjust the duty cycle for pulses produced by the waveform generator. (float)

 *property *frequency*: Any*

Control the output frequency (Hz)

 *property *high_impedance*: Any*

Set output impedance to HighZ. Displayed voltages are then converted internally so they match what an infinite load would see, rather than 50 Ohms. See p. 82 of the manual for details.

 *property *load*: Any*

Set the output impedance for a selected channel. Infinite impedance is returned as 9.9e+37.

 *property *noise*: Any*

Configure the waveform generator to produce noise with the specified parameters :param ampl: (float) Peak to peak noise amplitude in V :param offset: (float) DC noise offset in V

 *property *output_enabled*: Any*

Set or read the channel status. True indicates that the channel is on; False indicates that it is not.

 *property *pulse*: Any*

Configure the waveform generator to produce a pulse wave with the specified parameters. The duty cycle is set through the duty_cycle method. :param int freq: Frequency of the wave in Hz :param float ampl: Peak to peak amplitude of the wave in V :param float offset: DC offset of the wave in V :param float phase: Phase offset of the wave in degrees

 *property *pulse_width*: Any*

Adjust pulse width, in seconds, for pulses produced by the waveform generator.

 *property *shape*: Any*

Set or read the waveform type for the specified channel.

 *property *sine*: Any*

Configure the waveform generator to produce a sine with the specified parameters :param int freq: Frequency of the sine in Hz :param float ampl: Peak to peak amplitude of the sine in V :param float offset: DC offset of the sine in V :param float phase: Phase offset of the sine in degrees

 *property *square*: Any*

Configure the waveform generator to produce a square wave with the specified parameters :param int freq: Frequency of the wave in Hz :param float ampl: Peak to peak amplitude of the wave in V :param float offset: DC offset of the wave in V :param float phase: Phase offset of the wave in degrees

 *property *sync_enabled*: Any*

Set or read the synchronization flag. True means the channel triggers the synchronization connector; False means it does not.

 *property *triangle*: Any*

Configure the waveform generator to produce a triangle wave with the specified parameters :param int freq: Frequency of the wave in Hz :param float ampl: Peak to peak amplitude of the wave in V :param float offset: DC offset of the wave in V :param float phase: Phase offset of the wave in degrees

 *property *waveform*: Any*

Return a descriptor for the applied waveform.

## Rigol

### Rigol

This section documents the implemented Rigol instruments. For an instrument that is absent, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Rigol DG800 waveform generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/rigol/rigol_dg800.html)
  - [`DG800`](https://pymeasure.readthedocs.io/en/latest/api/instruments/rigol/rigol_dg800.html#pymeasure.instruments.rigol.DG800)
  - [`VoltageChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/rigol/rigol_dg800.html#pymeasure.instruments.rigol.rigol_dg800.VoltageChannel)
