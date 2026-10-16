# pymeasure.adapters.SerialAdapter

*class *pymeasure.adapters.SerialAdapter(*port*, *write_termination=''*, *read_termination=''*, ***kwargs*)

Bases: `Adapter`

Adapter for the Python Serial package that enables serial communication with an instrument.

Parameters:

- **port** (`Union`[`str`, `SerialBase`]) – Serial port

- **write_termination** (`str`) – String appended to each message before it is written. (default: `''`)

- **read_termination** (`str`) – String expected at the end of a read message, then removed from the returned text. (default: `''`)

- ****kwargs** – Any supported key-word argument for serial.Serial
