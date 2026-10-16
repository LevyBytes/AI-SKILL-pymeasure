# pymeasure.instruments.mksinst.mksinst.MKSInstrument

*class *pymeasure.instruments.mksinst.mksinst.MKSInstrument(*adapter*, *name='MKS Instrument'*, *address=253*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Abstract MKS Instrument

The device connection uses an RS232/RS485 serial link. These devices follow this communication protocol:

For a query, send ‘@&lt;aaa&gt;&lt;Command&gt;?;FF’ and expect ‘@&lt;aaa&gt;ACK&lt;Response&gt;;FF’. For a set command, send ‘@&lt;aaa&gt;&lt;Command&gt;!&lt;parameter&gt;;FF’ and expect ‘@&lt;aaa&gt;ACK&lt;Response&gt;;FF’. The &lt;aaa&gt; field is an address from 001 to 254 supplied during initialization. Because pyvisa cannot use ‘;FF’ as the terminator, this class replaces the normal communication methods.

Parameters:

- **adapter** – pyvisa resource name for the instrument, or an adapter instance

- **name** (*string*) – Instrument name.

- **address** – address inserted into each device message (default=253) (default: `253`)

- **kwargs** – Any key-word argument accepted by Instrument
