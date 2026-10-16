# pymeasure.instruments.ni.virtualbench.VirtualBench.MixedSignalOscilloscope.read_analog_digital_u64

[Owning MixedSignalOscilloscope contract](overview.md)

read_analog_digital_u64()

Transfers data from the instrument when acquisition state is Acquisition Complete. If the state is Running or Triggered, the method waits until Acquisition Complete; if the state is Stopped, it returns an error.

Returns:

Analog data out, analog data stride, analog t0, digital data out, digital timestamps out, digital t0, trigger timestamp, trigger reason

Return type:

(list, int, pyvb.Timestamp, list, list, pyvb.Timestamp, pyvb.Timestamp, enum)
