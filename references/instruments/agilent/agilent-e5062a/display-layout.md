# pymeasure.instruments.agilent.AgilentE5062A.display_layout

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *display_layout*: Any*

Set or read the display arrangement for windows (channels) (str). Valid options are listed below:

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

Generally, a number means the corresponding channel is visible, while ‘_’ marks a vertical split. Repeating a number gives that channel a larger window than the others. See Figure 3-1 in the programmer’s manual for details.

This layout splits multiple *channels*, not traces. Basic S-param measurements usually use one channel with multiple *traces*. See e.g. `AgilentE5062A.channels[1].visible_traces`
