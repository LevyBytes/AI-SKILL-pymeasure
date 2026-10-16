# Instruments with similar features

For instruments that share many features, inherit common behavior from a parent instrument class instead of duplicating code.

Note

Remember to adjust the instrument's `name` attribute: pass the right argument to `super().__init__()` when that option exists, or set the attribute again after the call.

Sometimes a derived instrument only adds new properties or methods. Other times, existing properties or methods must be fully redefined in the subclass. When only selected details differ, dynamic properties provide a concise solution.
