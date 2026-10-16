# pymeasure.instruments.siglenttechnologies.siglent_sds1072cml.VoltageChannel.get_descriptor

[Owning PyMeasure class, adapter and connection contract](overview.md)

get_descriptor(*descriptor=None*)

Return the descriptor for waveform data sent by the device query. If a raw byte stream descriptor is supplied, decode that value; otherwise, query the device for it. :return: dict: A dictionary with the keys: - numDataPoints: point count in the waveform - verticalGain: voltage increment per code value (in V) - verticalOffset: voltage offset added to decoded voltage values - horizInterval: time interval between points in s - horizOffset: offset added to time steps - descriptorOffset: Length of the C1:WF ALL,#9000000346 message
