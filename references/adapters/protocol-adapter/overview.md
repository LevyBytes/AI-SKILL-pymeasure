# pymeasure.adapters.ProtocolAdapter

*class *pymeasure.adapters.ProtocolAdapter(*comm_pairs=None*, *connection_attributes=None*, *connection_methods=None*, ***kwargs*)

Bases: `Adapter`

Testing adapter for the command exchange protocol without requiring instrument hardware.

Use this adapter mainly with `pymeasure.test.expected_protocol()`.

The `connection` attribute uses a `unittest.mock.MagicMock`, so each invoked member returns normally. To define a result, assign `adapter.connection.some_method.return_value = 7`; then `adapter.connection.some_method()` returns 7. You can also confirm the connection method ran with `assert adapter.connection.some_method.called is True`. Dictionaries may supply return values for attributes and methods.

Parameters:

- **comm_pairs** (*list*) - List of reference message-pair tuples. In each tuple, the first entry is sent to the instrument and the second entry is the reply. `None` marks a missing pair member, either write or read. Termination characters are **not** part of the messages.

- **connection_attributes** (`Optional`[`dict`]) - Dictionary containing connection attributes with their values. (default: `None`)

- **connection_methods** (`Optional`[`dict`]) - Dictionary mapping connection method names to the values they return. (default: `None`)
