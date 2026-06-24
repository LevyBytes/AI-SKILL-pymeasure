# Dsp7265

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Scope covered: DSP 7265 Lock-in Amplifier; Signal Recovery.

## DSP 7265 Lock-in Amplifier

### DSP 7265 Lock-in Amplifier

 *class *pymeasure.instruments.signalrecovery.DSP7265(*adapter*, *name='Signal Recovery DSP 7265'*, ***kwargs*)

Bases: `DSPBase`

Models the Signal Recovery DSP 7265 lock-in amplifier.

This class derives its commands from DSPBase and uses dynamic properties for multiple properties, with extra behavior layered on.

```python
lockin7265 = DSP7265("GPIB0::12::INSTR")
lockin7265.imode = "voltage mode"       # Set to measure voltages
lockin7265.reference = "internal"       # Use internal oscillator
lockin7265.fet = 1                      # Use FET pre-amp
lockin7265.shield = 0                   # Ground shields
lockin7265.coupling = 0                 # AC input coupling
lockin7265.time_constant = 0.10         # Filter time set to 100 ms
lockin7265.sensitivity = 2E-3           # Sensitivity set to 2 mV
lockin7265.frequency = 100              # Set oscillator frequency to 100 Hz
lockin7265.voltage = 1                  # Set oscillator amplitude to 1 V
lockin7265.gain = 20                    # Set AC gain to 20 dB
print(lockin7265.x)                     # Measure X channel voltage
lockin7265.shutdown()                   # Instrument shutdown

```

 *property *adc1*: Any*

Read the rear-panel ADC1 input voltage.

The return is a floating point voltage value in volts.

 *property *adc2*: Any*

Read the rear-panel ADC2 input voltage.

The return is a floating point voltage value in volts.

 *property *adc3

Measure the ADC3 input voltage.

 *property *adc3_time

Set or query ADC3 sample time, expressed in seconds.

 *property *auto_gain

Trigger automatic AC gain control on the lock-in amplifier.

 auto_phase()

Tune the reference absolute phase so X channel output is maximized while Y channel output signals are minimized.

 auto_sensitivity()

Set the full-scale sensitivity so the signal magnitude falls within 30 - 90 % of full-scale.

 buffer_to_float(*buffer_data*, *sensitivity=None*, *sensitivity2=None*, *raise_error=True*)

Translate fixed-point buffer data into floating point data.

Conversion is attempted for as many provided fields as possible. To convert every supplied column, the input data must meet specific conditions; when a key cannot be converted, it is either left out of the returned data or causes an exception, controlled by raise_error.

The conversion conditions are:

-

X, Y, magnitude, and noise conversion needs sensitivity data, supplied either inside the provided data or through the sensitivity argument.

-

X2, Y2, and magnitude2 follow the same rule, using sensitivity2.

-

Frequency conversion needs both ‘frequency part 1’ and ‘frequency part 2’.

Parameters:

-

**buffer_data** (*dict*) – Input data for conversion. It must match the get_buffer return format: a dict containing numpy arrays.

-

**sensitivity** – Optional sensitivity value for converting X, Y, magnitude, and noise. It may be a float or an array whose length matches the elements in buffer_data. When sensitivity is supplied and also exists in buffer_data, conversion uses the supplied value, while the buffer_data sensitivity is kept in the returned dict. (default: `None`)

-

**sensitivity2** – Mirrors the first sensitivity argument, applied to X2, Y2, magnitude2, and noise2. (default: `None`)

-

**raise_error** (*bool*) – Controls whether an exception is raised when any key in buffer_data cannot be converted. If False, unconvertible columns are excluded from the returned dict.

Returns:

Floating-point buffer data

Return type:

dict

 check_errors()

Fetch every instrument error and send each one to the log.

Returns:

`list` – List of error entries.

 check_get_errors()

After reading a property, check for errors and log what is found.

Used when that property has `check_get_errors=True`.

Override this method if some errors should raise an Exception.

Returns:

`list` – List of error entries.

 check_set_errors()

After writing a property, check for errors and log what is found.

Used when that property has `check_set_errors=True`.

Override this method if some errors should raise an Exception.

Returns:

`list` – List of error entries.

 clear()

Clears the instrument status byte

Return type:

`None`

 *property *complete

Get the synchronization bit.

This property synchronizes a controller with a device. The Operation Complete query adds ASCII character 1 to the device's Output Queue after all pending selected device operations have completed.

 *property *coupling*: Any*

Control the input coupling mode.

Accepted values are 0 for AC coupling mode and 1 for DC coupling mode.

 *property *curve_buffer_bits*: Any*

Choose which data outputs get saved into the curve buffer.

Accepted settings are integers from 1 through 65,535, or 2,097,151 in dual reference mode. (dynamic)

 *property *curve_buffer_interval*: Any*

Set the time spacing used when successive points are collected into the curve buffer.

The time interval accepts integer ms values at 5 ms resolution; inputs are rounded upward to a multiple of 5. Values may range from 0 through 1,000,000,000, which corresponds to 12 days. Setting the interval to 0 makes curve-buffer storage run at 1.25 ms/point (800 Hz), but only X and Y channel outputs can be stored. No CBD 3 command is needed for this setup because acquisition start performs it automatically.

 *property *curve_buffer_length*: Any*

Set the curve buffer length.

Accepted values are integers from 1 through 32,768. The effective maximum number of points depends on how many curves are stored, configured by the curve_buffer_bits property (32,768 / n).

 *property *curve_buffer_status*: Any*

Read the acquisition status for the curve buffer.

Four values come back: **First value - Curve Acquisition Status:** one of 5 status codes, where 0 means no activity, 1 means acquisition via TD command running, 2 means acquisition by a TDC command running, 5 means acquisition via TD command halted, and 6 means acquisition bia TDC command halted. **Second value - Number of Sweeps Acquired**: sweeps already acquired. **Third value - Status Byte:** decimal form of the status byte; ST returns the same response. **Fourth value - Number of Points Acquired:** points in the curve buffer that have been acquired.

 *property *dac1*: Any*

Set the rear-panel DAC1 output voltage.

Accepted values are floating point numbers from -12 to 12 V.

 *property *dac2*: Any*

Set the rear-panel DAC2 output voltage.

Accepted values are floating point numbers from -12 to 12 V.

 *property *dac3*: Any*

Set the rear-panel DAC3 output voltage.

Accepted values are floating point numbers from -12 to 12 V.

 *property *dac4*: Any*

Set the rear-panel DAC4 output voltage.

Accepted values are floating point numbers from -12 to 12 V.

 *property *fet*: Any*

Select the transistor type for the voltage preamplifier.

Accepted values are 0 for bipolar and 1 for FET.

 *property *frequency*: Any*

Control the oscillator frequency.

Accepted values are floating point numbers that represent frequency in Hz. (dynamic)

 *property *gain

Set the AC gain for the signal channel amplifier.

 get_buffer(*quantity=None*, *convert_to_float=True*, *wait_for_buffer=True*)

Fetch the buffer once filling is complete. Data read from the lock-in uses fixed-point format, so it must be translated before it represents meaningful data. If convert_to_float is True, conversion runs before data is returned when conversion is possible.

Parameters:

-

**quantity** (*str*) – Optional name of the curve-buffer quantity to retrieve. Single-channel choices are ‘x’ and ‘y’; vector choices are ‘magnitude’ and ‘phase’; input choices are ‘sensitivity’, ‘adc1’, ‘adc2’, and ‘adc3’; output choices are ‘dac1’ and ‘dac2’; other choices are ‘noise’, ‘ratio’, ‘log ratio’, ‘event’, ‘frequency part 1’, and ‘frequency part 2’. In both dual modes, the additional choices are ‘x2’, ‘y2’, ‘magnitude2’, ‘phase2’, and ‘sensitivity2’. When quantity is not provided, all available data is retrieved.

-

**convert_to_float** (*bool*) – Boolean switch for converting fixed-point buffer-data into meaningful floating point values through buffer_to_float. If True, the method attempts conversion for every available data field and raises an exception when that cannot be done. If False, conversion is skipped and raw buffer-data is returned.

-

**wait_for_buffer** (*bool*) – Boolean switch for waiting when this method is called before data acquisition has finished. If True, execution waits until the buffer is full before proceeding. If False, an exception is raised when acquisition is still incomplete at call time.

 *property *harmonic*: Any*

Control the reference harmonic mode.

Valid values are integers. (dynamic)

 *property *id*: Any*

Read the instrument model number.

Returned value is an integer.

 *property *imode*: Any*

Configure the lock-in amplifier to detect either a voltage signal or a current signal.

Allowed selections are `voltage mode, ``current mode`, or `low noise current mode`.

 init_curve_buffer()

Initialize curve storage memory and status variables, deleting all records of curves taken earlier.

 *property *log_ratio*: Any*

Read log (base 10) for the ratio of X channel to ADC1.

The result is unitless, uses floating point form, and equals log(X/ADC1).

 *property *mag*: Any*

Read the signal magnitude.

The return is a floating point voltage value in volts.

 *property *next_error

Read the instrument's next error as a tuple containing code and message.

 *property *options

Get the device options installed.

 *property *phase*: Any*

Read the signal absolute phase angle.

The return is a floating point angle in degrees.

 *property *ratio*: Any*

Read the ratio of X channel to ADC1.

The result is unitless, uses floating point form, and equals X/ADC1.

 read(***kwargs*)

Read the response, then strip the extra unicode character from instrument readings.

 read_binary_values(***kwargs*)

Read binary values supplied by the device.

 read_bytes(*count*, ***kwargs*)

Read a specified byte count from the instrument.

Parameters:

-

**count** (*int*) – Number of bytes requested. The value -1 means read the complete read buffer.

-

**kwargs** – Keyword arguments passed to the adapter.

Returns bytes:

Instrument byte response, including termination.

Return type:

`bytes`

 *property *reference*: Any*

Set the oscillator reference input mode.

Accepted values are `internal`, `external rear`, or `external front`.

 *property *reference_phase*: Any*

Set the reference absolute phase angle.

Accepted values are floating point numbers from 0 - 360 degrees.

 reset()

Resets the instrument.

Return type:

`None`

 *property *sensitivity

Set the measurement sensitivity range for the signal.

In voltage measurement mode, accepted values are discrete choices spanning 2 nV through 1 V. For current measurement mode, the discrete choices start at 2 fA and extend to 1 µA in normal current mode; in low noise current mode, they extend up to 10 nA.

 setChannelAMode()

Configure the lock-in amplifier to measure a voltage signal only through the A input connector.

 setDifferentialMode(*lineFiltering=True*)

Configure the lock-in amplifier for differential mode, measuring A-B.

 set_buffer(*points*, *quantities=None*, *interval=0.01*)

Ready the curve buffer for a measurement.

Parameters:

-

**points** (*int*) – Number of points that will be recorded in the curve buffer

-

**quantities** (*list*) – List of string quantities to record in the curve buffer. Choices include ‘x’ and ‘y’; ‘magnitude’ and ‘phase’; ‘sensitivity’, ‘adc1’, ‘adc2’, and ‘adc3’; ‘dac1’ and ‘dac2’; ‘noise’, ‘ratio’, ‘log ratio’, and ‘event’; plus ‘frequency’ (or ‘frequency part 1’ and ‘frequency part 2’). In both dual modes, additional choices are ‘x2’, ‘y2’, ‘magnitude2’, ‘phase2’, and ‘sensitivity2’. Default is ‘x’ and ‘y’.

-

**interval** (*float*) – Time, in s, separating consecutive curve-buffer points. Default is 10 ms.

 set_voltage_mode()

Configure the lock-in amplifier to measure a voltage signal.

 *property *shield*: Any*

Set the input connector shield state.

Accepted values are 0 for shields grounded and 1 for shields floating, i.e., connected to ground through a 1 kOhm resistor.

 shutdown()

Shut down the lock-in amplifier safely.

Set oscillator amplitude to 0 V and AC gain to 0 dB.

 *property *slope*: Any*

Set the low-pass filter roll-off.

Accepted values are integers 6, 12, 18, or 24, representing the low-pass filter slope in dB/octave.

 start_buffer()

Start data acquisition. Acquisition begins at the current curve-buffer position and proceeds at the rate configured by the STR command until the buffer fills.

 *property *status

Read the status byte and Master Summary Status bit.

 *property *time_constant*: Any*

Control the filter time constant.

Accepted values are a fixed set of time constants from 10 us through 50,000 s. Returned values are floating point numbers measured in seconds.

 *property *voltage*: Any*

Control the oscillator amplitude.

Accepted values are floating point numbers from 0 to 5 V.

 wait_for(*query_delay=None*)

Pause for a specified time. ‘ask’ uses this wait before reading.

Parameters:

**query_delay** (`Optional`[`float`]) – Delay between writing and reading, in seconds. None uses the default delay. (default: `None`)

Return type:

`None`

 wait_for_buffer(*timeout=None*, *delay=0.1*)

Wait until the curve buffer has filled.

 write(*command*, ***kwargs*)

Send a string command to the instrument, appending write_termination.

Parameters:

-

**command** (`str`) – command string sent to the instrument

-

**kwargs** – Keyword arguments passed to the adapter.

Return type:

`None`

 write_binary_values(*command*, *values*, **args*, ***kwargs*)

Send binary values to the device.

Parameters:

-

**command** (`str`) – Command to send.

-

**values** (`Sequence`[`Union`[`int`, `float`]]) – Values to transmit.

-

****kwargs** (**args**,*) – Additional arguments passed through to the Adapter.

Return type:

`None`

 write_bytes(*content*, ***kwargs*)

Write byte content to the instrument.

Return type:

`None`

 *property *x*: Any*

Read the output signal X channel.

The return is a floating point voltage value in volts.

 *property *xy*: Any*

Read both X and Y channels.

The returns are floating point voltage values in volts.

 *property *y*: Any*

Read the output signal Y channel.

The return is a floating point voltage value in volts.

## Signal Recovery

### Signal Recovery

This section documents the implemented Signal Recovery instruments. For an instrument that is not listed, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

- Listed: [DSP 7225 Lock-in Amplifier](https://pymeasure.readthedocs.io/en/latest/api/instruments/signalrecovery/dsp7225.html)
  - [`DSP7225`](https://pymeasure.readthedocs.io/en/latest/api/instruments/signalrecovery/dsp7225.html#pymeasure.instruments.signalrecovery.DSP7225)

- Listed: [DSP 7265 Lock-in Amplifier](https://pymeasure.readthedocs.io/en/latest/api/instruments/signalrecovery/dsp7265.html)
  - [`DSP7265`](https://pymeasure.readthedocs.io/en/latest/api/instruments/signalrecovery/dsp7265.html#pymeasure.instruments.signalrecovery.DSP7265)
