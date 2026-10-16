# pymeasure.test.expected_protocol

[Owning PyMeasure class, adapter and connection contract](../../adapters/prologix-adapter/overview.md)

pymeasure.test.expected_protocol(*instrument_cls*, *comm_pairs*, *connection_attributes=None*, *connection_methods=None*, ***kwargs*)

Context manager for checking instrument commands sent and received when no device is attached.

Provide the instrument class plus expected command-response pairs; the context manager then checks that code inside the block sends the intended messages.

Protocol definitions omit terminators because those usually belong to the communication method, i.e. Adapter, rather than to the protocol.

Parameters:

- **instrument_cls** (*pymeasure.Instrument*) – [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument) subclass that will be instantiated.

- **comm_pairs** (*list**[**2-tuples**[**str**]**]*) – Command-response pair list, i.e. 2-tuples such as (‘VOLT?’, ‘3.14’). ‘None’ marks a missing pair member (command or response), for example (None, ‘RESP1’). Termination characters are not included in commands or responses.

- **connection_attributes** (`Optional`[`dict`[`str`, `Any`]]) – Dictionary mapping connection attributes to their values. (default: `None`)

- **connection_methods** (`Optional`[`dict`[`str`, `Any`]]) – Dictionary mapping connection method names to their return values. (default: `None`)

- ****kwargs** – Keyword arguments used when instantiating the instrument.

Return type:

`Generator`[`TypeVar`(`Inst`, bound= [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)), `Any`, `None`]
