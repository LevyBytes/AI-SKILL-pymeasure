# pymeasure.instruments.advantest.advantestR624X.SMUChannel.sample_hold_mode

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *sample_hold_mode*: Any*

Configure the measurement integration time (`MST`).

Type:

`SampleHold`

Note

- Only valid for pulse measurement and pulse sweep measurement.

- In sample hold mode, AD transformation occurs immediately before the pulse width falls.

- Sample hold mode cannot be configured during DC measurement or DC sweep measurement. In sample-and-hold mode, integration time is 100 µs. In 2-channel synchronous operation, when one channel performs pulse generation and the other uses sample-and-hold mode, the DC measurement side also runs in sample-and-hold mode.

-
For pulse or pulse-sweep operation, the WT command settings for pulse width (Tw), pulse period (Tp), and measure delay time (Td) must stay within their allowed limits. If those limits are missed, integration time will not change. To increase integration time, adjust pulse width (Tw) and pulse period (Tp) first; to reduce pulse width and pulse cycle, reduce integration time first.
