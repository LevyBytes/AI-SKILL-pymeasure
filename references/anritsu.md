# Anritsums9710C, Anritsums2090A, Anritsumg3692C

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Coverage includes Anritsu MS9710C Optical Spectrum Analyzer, Anritsu, Anritsu MS2090A Handheld Spectrum Analyzer, and Anritsu MG3692C Signal Generator.

## Anritsu MS9710C Optical Spectrum Analyzer

### Anritsu MS9710C Optical Spectrum Analyzer

 *class *pymeasure.instruments.anritsu.AnritsuMS9710C(*adapter*, *name='Anritsu MS9710C Optical Spectrum Analyzer'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Anritsu MS9710C Optical Spectrum Analyzer.

 *property *analysis*: Any*

Control Analysis Control

 *property *analysis_result*: Any*

Retrieve the analysis result from the current scan.

 *property *average_point*: Any*

Set the number of averages for each point to 2-1000, or OFF.

 *property *average_sweep*: Any*

Set the sweep averaging count to 2-1000, or OFF.

 center_at_peak(***kwargs*)

Move the measured peak to the spectrum center.

 *property *data_memory_a_condition*: Any*

Return data memory register A conditions: starting wavelength and sampling point (l1, l2, n).

 *property *data_memory_a_size*: Any*

Return how many sampled points are stored in data memory register A.

 *property *data_memory_a_values*: Any*

Return binary data from memory register A.

 *property *data_memory_b_condition*: Any*

Return data memory register B conditions: starting wavelength and sampling point (l1, l2, n).

 *property *data_memory_b_size*: Any*

Return how many sampled points are stored in data memory register B.

 *property *data_memory_b_values*: Any*

Return binary data from memory register B.

 *property *data_memory_select*: Any*

Control Memory Data Select.

 *property *dip_search*: Any*

Control Dip Search Mode

 *property *ese2*: Any*

Control Extended Event Status Enable Register 2

 *property *esr2*: Any*

Control Extended Event Status Register 2

 *property *level_lin*: Any*

Control Level Linear Scale (/div)

 *property *level_log*: Any*

Control Level Log Scale (/div)

 *property *level_opt_attn*: Any*

Set Optical Attenuation Status (ON/OFF).

 *property *level_scale*: Any*

Get Current Level Scale

 *property *measure_mode*: Any*

Return the OSA's current Measure Mode.

 measure_peak()

Measure the peak, then return the trace marker.

 *property *peak_search*: Any*

Control Peak Search Mode

 read_memory(*slot='A'*)

Load the scan stored in a memory slot.

 *property *resolution*: Any*

Control Resolution (nm)

 *property *resolution_actual*: Any*

Control Resolution Actual (ON/OFF)

 *property *resolution_vbw*: Any*

Control Video Bandwidth Resolution

 *property *sampling_points*: Any*

Control number of sampling points

 single_sweep(***kwargs*)

Run one sweep and block until completion.

 *property *trace_marker*: Any*

Position the trace marker by wavelength; return trace wavelength and power.

 *property *trace_marker_center*: Any*

Set Trace Marker at Center. Use 1 or True to initiate command.

 wait(*n=3*, *delay=1*)

Query OPC Command and wait for the appropriate response.

 wait_for_sweep(*n=20*, *delay=0.5*)

Block until a sweep stops.

Checks bit 1 of the ESR2 to perform this.

 *property *wavelength_center*: Any*

Set Center Wavelength of Spectrum Scan in nm.

 *property *wavelength_marker_value*: Any*

Set Wavelength Marker Value (wavelength or freq.?).

 *property *wavelength_span*: Any*

Set Wavelength Span of Spectrum Scan in nm.

 *property *wavelength_start*: Any*

Set Wavelength Start of Spectrum Scan in nm.

 *property *wavelength_stop*: Any*

Set Wavelength Stop of Spectrum Scan in nm.

 *property *wavelength_value_in*: Any*

Set Wavelength value in Vacuum or Air.

 *property *wavelengths

Return a numpy array containing the current scan wavelengths.

## Anritsu

### Anritsu

This section documents the implemented Anritsu instruments. For an instrument not listed here, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- [Anritsu MG3692C Signal Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMG3692C.html)
  - [`AnritsuMG3692C`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMG3692C.html#pymeasure.instruments.anritsu.AnritsuMG3692C)

- [Anritsu MS9710C Optical Spectrum Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS9710C.html)
  - [`AnritsuMS9710C`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS9710C.html#pymeasure.instruments.anritsu.AnritsuMS9710C)

- [Anritsu MS9740A Optical Spectrum Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS9740A.html)
  - [`AnritsuMS9740A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS9740A.html#pymeasure.instruments.anritsu.AnritsuMS9740A)

- [Anritsu MS2090A Handheld Spectrum Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS2090A.html)
  - [`AnritsuMS2090A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS2090A.html#pymeasure.instruments.anritsu.AnritsuMS2090A)

- [Anritsu MS464xB Vector Network Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS464xB.html)
  - [`AnritsuMS4642B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS464xB.html#pymeasure.instruments.anritsu.AnritsuMS4642B)
  - [`AnritsuMS4644B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS464xB.html#pymeasure.instruments.anritsu.AnritsuMS4644B)
  - [`AnritsuMS4645B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS464xB.html#pymeasure.instruments.anritsu.AnritsuMS4645B)
  - [`AnritsuMS4647B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS464xB.html#pymeasure.instruments.anritsu.AnritsuMS4647B)
  - [`AnritsuMS464xB`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS464xB.html#pymeasure.instruments.anritsu.AnritsuMS464xB)
  - [`MeasurementChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS464xB.html#pymeasure.instruments.anritsu.anritsuMS464xB.MeasurementChannel)
  - [`Trace`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS464xB.html#pymeasure.instruments.anritsu.anritsuMS464xB.Trace)
  - [`Port`](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS464xB.html#pymeasure.instruments.anritsu.anritsuMS464xB.Port)

## Anritsu MS2090A Handheld Spectrum Analyzer

### Anritsu MS2090A Handheld Spectrum Analyzer

 Class constructor: *pymeasure.instruments.anritsu.AnritsuMS2090A* with *adapter*, *name='Anritsu MS2090A Handheld Spectrum Analyzer'*, and ***kwargs*.

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Anritsu MS2090A Handheld Spectrum Analyzer.

 abort()

Initiate a sweep/measurement.

 *property *active_state*: Any*

When the state is "set", the instrument is being used by someone.

 *property *external_current*: Any*

Query the actual bias current in A.

 *property *fetch_control*: Any*

Return the Control Channel measurement in json format.

 *property *fetch_density*: Any*

Return the latest channel density measurement.

 *property *fetch_eirpower*: Any*

Return the current EIRP, Max EIRP, Horizontal EIRP, and the Vertical and Sum EIRP results in dBm.

 *property *fetch_eirpower_data*: Any*

Return the current EIRP measurement result in dBm.

 *property *fetch_eirpower_max*: Any*

Return the Max EIRP measurement result in dBm.

 *property *fetch_emf*: Any*

Return current EMF measurement data in JSON format.

 *property *fetch_emf_meter*: Any*

Return live EMF measurement data in JSON format.

 *property *fetch_emf_meter_sample*: Any*

Return EMF measurement data for a specified sample number in JSON format.

 *property *fetch_interference_power*: Any*

Fetch Interference Finder Integrated Power.

 *property *fetch_mimo_antenas*: Any*

Return the sync power measurement in json format.

 *property *fetch_ocupied_bw*: Any*

Return different measurement information sets depending on the suffix.

 *property *fetch_ota_mapping*: Any*

Return the latest Coverage Mapping measurement result.

 *property *fetch_pan*: Any*

Return current Pulse Analyzer measurement data in JSON format.

 *property *fetch_pbch_constellation*: Any*

Return the latest Physical Broadcast Channel constellation hitmap.

 *property *fetch_pci*: Any*

Returns PCI measurements

 *property *fetch_pdsch*: Any*

Return Data Channel Measurements in JSON format.

 *property *fetch_pdsch_constellation*: Any*

Return the latest Physical Downlink Shared Channel constellation.

 *property *fetch_peak*: Any*

Return a pair of peak amplitude values in the current sweep.

 *property *fetch_power*: Any*

Return the latest channel power measurement.

 *property *fetch_rrm*: Any*

Return Radio Resource Management in JSON format.

 *property *fetch_scan*: Any*

Return cell scanner measurements in JSON format.

 *property *fetch_semask*: Any*

Return the current Spectral Emission Mask measurement result.

 *property *fetch_ssb*: Any*

Returns the SSB measurement

 *property *fetch_sync_evm*: Any*

Return Sync EVM measurement in JSON format.

 *property *fetch_sync_power*: Any*

Return sync power measurements in JSON format.

 *property *fetch_tae*: Any*

Return Time Alignment Error in JSON format.

 *property *frequency_center*: Any*

Set the center frequency in Hz.

 *property *frequency_offset*: Any*

Set the frequency offset in Hz.

 *property *frequency_span*: Any*

Set the frequency span in Hz.

 *property *frequency_span_full*: Any*

Set the frequency span to full span.

 *property *frequency_span_last*: Any*

Restore the frequency span to the previous span value.

 *property *frequency_start*: Any*

Set the start frequency in Hz.

 *property *frequency_step*: Any*

Set or query the step size used to gradually increase or decrease frequency values in Hz.

 *property *frequency_stop*: Any*

Set the start frequency in Hz.

 *property *gps*: Any*

Return the device timestamp, latitude, and longitude.

 *property *gps_all*: Any*

Return the fix timestamp, latitude, longitude, altitude, and information on the sat used.

 *property *gps_full*: Any*

Return the device timestamp, latitude, longitude, altitude, and satellite count.

 *property *gps_last*: Any*

Return the last fixed GPS result's timestamp, latitude, longitude, and altitude.

 init_all_sweep()

Initiate all sweep/measurement.

 *property *init_continuous*: Any*

Specify whether the sweep/measurement is triggered continuously.

 *property *init_spa_self*: Any*

Run a self-test and return the results.

 init_sweep()

Initiate a sweep/measurement.

 *property *meas_acpower*: Any*

Use adjacent channel power ratio as the active measurement, apply the default measurement parameters, and trigger a new measurement. Return main channel power plus the lower adjacent, upper adjacent, lower alternate, and upper alternate channel power results.

 *property *meas_emf_meter_clear_all*: Any*

Clear EMF measurement data for all samples. If sampling state was on, it will be turned off.

 *property *meas_emf_meter_clear_sample*: Any*

Clear EMF measurement data for a specified sample number. If the specified sample is currently active, sampling state will be turned off.

 *property *meas_emf_meter_sample*: Any*

Start or Stop applying measurement results to the currently selected sample.

 *property *meas_int_power*: Any*

Use interference finder as the active measurement, apply the default measurement parameters, trigger a new measurement, and return integrated power as the result. This combines :CONFigure:INTerference; :READ:INTerference:POWer?

 *property *meas_iq_capture*: Any*

Use this set command to start the IQ capture measurement.

 *property *meas_iq_capture_fail*: Any*

Set or query whether the instrument automatically saves an IQ capture when losing sync.

 *property *meas_ota_mapp*: Any*

Use OTA Coverage Mapping as the active measurement, apply the default measurement parameters, trigger a new measurement, and return the measured values.

 *property *meas_ota_run*: Any*

Turn OTA Coverage Mapping Data Collection on/off. The command is effective only when the instrument is in Coverage Mapping measurement.

 *property *meas_power*: Any*

Use channel power as the active measurement, apply the default measurement parameters, trigger a new measurement, and return channel power as the result. This combines :CONFigure:CHPower; :READ:CHPower:CHPower?

 *property *meas_power_all*: Any*

Use channel power as the active measurement, apply the default measurement parameters, trigger a new measurement, and return the channel power and channel power density results. This combines :CONFigure:CHPower; :READ:CHPower?

 *property *power_density*: Any*

Use channel power as the active measurement, apply the default measurement parameters, trigger a new measurement, and return channel power density as the result. This combines :CONFigure:CHPower; :READ:CHPower:DENSity?

 *property *preamp*: Any*

Set the preamp state. Note that this may change the reference level and/or attenuation.

 *property *sense_mode*: Any*

Configure the operational mode of the Spa app.

 *property *view_sense_modes*: Any*

Return available modes for the Spa application. The mode names are comma-separated in the response. See command [:SENSe]:MODE for the mode name specification.

## Anritsu MG3692C Signal Generator

### Anritsu MG3692C Signal Generator

 *class *pymeasure.instruments.anritsu.AnritsuMG3692C(*adapter*, *name='Anritsu MG3692C Signal Generator'*, ***kwargs*)

Bases: `SCPIUnknownMixin`, [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Model for the Anritsu MG3692C Signal Generator.

 disable()

Disables the signal output.

 enable()

Enables the signal output.

 *property *frequency*: Any*

Set or read the output frequency in Hz. This property can be set. (float)

 *property *output

Set or read the signal output state. (bool)

 *property *power*: Any*

Set or read the output power in dBm. (float))

 shutdown()

Shut down the instrument and place it in a safe state.
