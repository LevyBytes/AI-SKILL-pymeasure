# pymeasure.instruments.agilent.agilentE5062A.VNAChannel.display_layout

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *display_layout*: Any*

Set or read trace graph layout within the channel (str). This does not change which traces are active. Valid options are:

- D1

- D12

- D1_2

- D112

- D1_1_2

- D123

- D1_2_3

- D12_33

- D11_23

- D13_23

- D12_13

- D1234

- D1_2_3_4

- D12_34

Generally, a number means the corresponding trace has its own subplot, while ‘_’ indicates a vertical split. Repeating a number makes that trace window larger than the others. See Figure 3-1 in the programmer’s manual for details. If a trace is active but its number is absent from the `display_layout` identifier, it is drawn in the first subplot.

## Related property contracts

- Open when checking pymeasure.instruments.agilent.agilentE5062A.VNAChannel.frequencies: [frequencies](frequencies.md).
