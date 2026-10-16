# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.service_request_enable_register

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *service_request_enable_register*: Any*

Control the service request enable register (SRER) as `SRER` `IntFlag` (`*SRE`).

Note

Serial polling does not clear bits other than the RQS bit. When `power_on_clear()` is set, the registers cleared are the status byte enable register, SESER, device operation enable register, channel operation, and the enable register; no SRQ is issued.
