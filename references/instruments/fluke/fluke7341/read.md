# pymeasure.instruments.fluke.Fluke7341.read

[Owning PyMeasure class, adapter and connection contract](overview.md)

read()

Read until read_termination is encountered, excluding it, or return the whole read buffer.

Parse the value out of the response string.

Response strings follow “type: value optional information”. The optional information may include the unit, such as degree centigrade or Fahrenheit.
