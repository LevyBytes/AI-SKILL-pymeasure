# Enumerations

[Owning PyMeasure class, adapter and connection contract](../agilent-b1500-smuvoltage-ranging/overview.md)

Enumerations make available parameters easier to choose where applicable. Methods accept either a member name or number; use the name when readability matters. The instrument receives the member number. Calling string conversion on an enumeration member produces a title case string with whitespace separators (`__str__()`), and that string is not valid for selecting the enumeration member later. It is intended only for logging or documentation.
