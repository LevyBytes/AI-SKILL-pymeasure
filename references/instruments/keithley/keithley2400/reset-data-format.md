# pymeasure.instruments.keithley.Keithley2400.reset_data_format

[Owning PyMeasure class, adapter and connection contract](overview.md)

reset_data_format()

Restore the data format expected by `Keithley2400`.

Expected data format: [&lt;current&gt;, &lt;voltage&gt;, &lt;resistance&gt;, &lt;time&gt;, &lt;status&gt;].

Caution

Changing the data format after initialization with the ?:FORMAT:ELEMENTS? command can cause parts of `Keithley2400` to fail.
