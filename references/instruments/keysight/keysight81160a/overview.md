# pymeasure.instruments.keysight.Keysight81160A

Class constructor: pymeasure.instruments.keysight.Keysight81160A(adapter, **kwargs).
Default name: 'Agilent 33500 Function/Arbitrary Waveform generator family'.

Bases: [`Agilent33500`](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33500.html#pymeasure.instruments.agilent.Agilent33500)

Provide a high-level Python interface for controlling and querying the Keysight 81160A instrument.

```python
from pymeasure.instruments.keysight.keysight81160A import Keysight81160A

generator = Keysight81160A("GPIB::1")        # Replace with your device address
generator.reset()                            # Reset the generator to default settings

generator.shape = "SIN"                      # Set default channel output shape to sine
generator.channels[1].shape = "SIN"          # Set channel 1 output signal shape to sine
generator.frequency = 1e3                    # Set default channel output frequency to 1 kHz
generator.channels[1].frequency = 1e3        # Set channel 1 output frequency to 1 kHz
generator.channels[2].amplitude = 5          # Set channel 2 output amplitude to 5 Vpp
generator.channels[2].offset = 0.5           # Set channel 2 output offset to 0.5 V
generator.channels[2].output = True          # Enable channel 2 output

# Output a square wave at 1 kHz with 5 Vpp and 0.5 V offset
generator.channels[2].apply_square(1e3, 5, 0.5)

ch1 = generator.channels[1]                  # Short form for channel 1
waveform = [-2.0, -1.5, 0.0, 1.5, 2.0]       # Define a user-defined waveform in Volts
ch1.waveform_volatile = waveform             # Set user-defined waveform to volatile memory
print(f"{ch1.free_memory_slots} slots free") # Get number of slots in non-volatile memory
ch1.save_waveform(waveform, "test")          # Save the waveform to non-volatile memory
ch1.shape = "USER"                           # Set channel 1 shape to user-defined
ch1.trigger_mode = "MAN"                     # Set trigger mode to manual
ch1.trigger_count = 2                        # Set number of cycles to be generated to 2
ch1.output = True                            # Enable channel 1 output
generator.trigger()                          # Trigger the generator to output the waveform
ch1.delete_waveform("test")                  # Delete the waveform from non-volatile memory

```
