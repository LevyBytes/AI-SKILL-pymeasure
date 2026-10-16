# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.search_comparison_setup

[Owning PyMeasure class, adapter and connection contract](overview.md)

search_comparison_setup(*search_mode*, *occurrence_after_stop*, *channel*, *comparison*, *comparison_function*, *upper_limit*, *lower_limit*)

Configure search measurement comparison calculation (`MAR~;CMD~;NENT`).

Parameters:

- **search_mode** (int or `SearchMode`) – Search mode indicating binary/linear behavior and the sense/search channel.

- **occurrence_after_stop** (int or `OccurrenceAfterStop`) – Output behavior used after stopping.

- **channel** (*int*) – Channel number, 1 or 2; the instrument ignores it.

- **comparison** (int or `ComparisonMode`) – Comparison mode selector.

- **comparison_function** (int or `ComparisonValueType`) – Comparison value type selector.

- **upper_limit** (*float*) – Upper comparison limit.

- **lower_limit** (*float*) – Lower comparison limit.

Note

The instrument reports an error when the lower value exceeds the upper value.
