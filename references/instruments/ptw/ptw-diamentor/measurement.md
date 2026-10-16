# pymeasure.instruments.ptw.ptwDIAMENTOR.measurement

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *measurement*: Any*

Get the measurement result (dict).

Dict keys:

`dap`, `dap_rate`, `time`

The result includes the dose-area-product (DAP) and dose-area-product rate. Units for `dap` and `dap_rate` are determined by the `dap_unit` property. Time is reported in seconds.
