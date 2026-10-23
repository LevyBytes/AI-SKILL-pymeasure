# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.set_output_format - set_output_format complete four header-character tables

[Owning PyMeasure class, adapter and connection contract](overview.md) / [set_output_format signature, delimiters and terminator selection](output-format-parameters.md)

| 1st character header: |  |
| --- | --- |
| 1. | Normal measurement data |
| 1. | Measurement data during overrange |
| 1. | Compliance (limiter) is working. |
| 1. | Oscillation detection is working. |
| 1. | [Indicates the generated data] |
| 1. | Measurement data recorded when a search measurement error occurs |
| 1. | Measurement data is not saved in the buffer memory. |

| 2nd character header: |  |
| --- | --- |
| 1. | A-channel data for asynchronous operation (A-channel generation data) |
| 1. | B-channel data during asynchronous operation (B channel generation data) |
| 1. | A-channel data used for synchronous, sweeping, delayed sweep, and double synchronous sweep operations. |
| 1. | B-channel data used for synchronous, sweeping, delayed sweep, and double synchronous sweep operations. |

| 3rd character header: |  |
| --- | --- |
| 1. | Current generation, voltage measurement (ISVM) [Current generation] |
| 1. | Voltage generation, current measurement (VSIM) [Voltage generation] |
| 1. | Current generation, current measurement (ISIM) |
| 1. | Voltage generation, voltage measurement (VSVM) |
| 1. | Current generation with external voltage measurement (IS, EXT, VM) |
| 1. | Voltage generation, external current measurement (VS, EXT, IM) |
| 1. | Current generation with external current measurement (IS, EXT. IM) |
| 1. | Voltage generation, external voltage measurement (VS, EXT, VM) |
| 1. | Measurement data is not saved in the buffer memory. |

| 4th character header: |  |
| --- | --- |
| 1. | No operation (fixed to A) |
| 1. | Null operation result |
| 1. | Comparison operation result is GO. |
| 1. | Comparison operation result is LO. |
| 1. | Comparison operation result is HI. |
| 1. | Null operation + comparison operation result is GO. |
| 1. | Null operation + comparison operation result is LO. |
| 1. | Null operation + comparison operation result is HI. |
| 1. | Measurement data is not saved in the buffer memory. |
