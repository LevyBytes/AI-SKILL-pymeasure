# Your instrument’s user interface

An instrument exposes properties and methods to users; those members should be visible through the documentation and an editor's autocomplete.

Aside from standard SCPI properties such as `id`, you generally decide how to shape this interface. A few conventions have proven worth following:

- Names matter. Choose clear, expressive, and unambiguous names for the elements on your instrument.

- When pymeasure already has comparable instruments in the same "family" (for example, a power supply), follow those patterns where they apply. Prefer all power supplies using `current_limit` over a mixture such as `current_max`, `Ilim`, `max_curr`, etc.

- When another instrument already uses a similar command set, consider inheriting from it and changing only the few differences. That greatly cuts duplicate code and maintenance load. The [Instruments with similar features](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#instruments-with-similar-features) section explains the approach.

- Most of an instrument interface will likely consist of properties for quantities that are set, read, or both. PyMeasure's custom properties (see [Writing properties](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#properties) ff. below) provide convenience behavior and are preferred, while plain Python properties remain acceptable.

- "Actions", commands, or verbs normally belong as methods rather than properties: `recall()`, `trigger_scan()`, `prepare_resistance_measurement()`, etc.

- Keeping properties separate from methods also supports the ["command-query separation" principle](https://en.wikipedia.org/wiki/Command%E2%80%93query_separation).

- For instruments with multiple identical channels, consult [Instruments with channels](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html#channels).

You may define whatever methods are needed to interact with the instrument. In those methods, send commands through `self.ask(command)`, `self.write(command)`, and `self.read()` rather than directly invoking the adapter. If communication requires modified sent or received commands, override these methods in the instrument; see [Advanced communication protocols](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/advanced_communication.html#advanced-communication-protocols) for more information.

The project has accumulated best practices that make instruments simpler to author and maintain. The following sections describe them, and following them is strongly encouraged.
