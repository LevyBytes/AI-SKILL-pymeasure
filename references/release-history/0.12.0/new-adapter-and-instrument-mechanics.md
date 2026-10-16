# Version 0.12.0 (2023-07-05) — New adapter and instrument mechanics

- Every instrument constructor must accept a `name` argument.

- Changed: by default, Adapter `read_bytes` no longer stops at a termination character unless `break_on_termchar` is True.

- The Channel class was added. `Instrument.channels` and `Instrument.ch_X`, where `X` is any channel name, are reserved for channel mechanics.

- The `check_get_errors` and `check_set_errors` parameters enable calls to same-named methods, making it easier to handle instruments that acknowledge each “set” command.

- The Channel feature was added to instruments (@bmoneke, mcdo0486, #718, #761, #852, #931).

- The `values` method gained a `maxsplit` parameter (@bmoneke, #793).

- A deprecated global preprocess reply path was added for backward compatibility (@bmoneke, #876).

- VISAAdapter gained a fallback version for discarding the read buffer (@dkriegner, #836).

- SerialAdapter gained `flush_read_buffer` (@RobertoRoos, #865).

- PrologixAdapter gained `gpib_read_timeout` (@neuschs, #927).

- A command-line option was added to pass a resource address for instrument tests (@bleykauf, #789).

- Testing support now includes “find all instruments” plus channels (@bmoneke, #909, @mcdo0486, #911, #912).

- A test now confirms that an instrument passes kwargs to its adapter (@bmoneke, #814).

- Adds property docstring check (@bmoneke, #895)

- Improves property factories’ docstrings (@bmoneke, #843)

- Property factories were improved so undefined kwargs are rejected (@bmoneke, #856).

- Property factories were improved with check_set/get_errors support for invoking same-named methods (@bmoneke, #883).

- Adapter `read_bytes` was improved (@bmoneke, #839).

- ProtocolAdapter was improved with a mock connection (@bmoneke, #782), and protocols can now contain empty messages (@bmoneke, #818).

- Prologix adapter documentation was improved (@bmoneke, #813), and configurable settings were added (@bmoneke, #845).

- `SerialAdapter` behavior for `read_bytes(-1)` was improved (@RobertoRoos, #866).

- All instruments were improved with the name kwarg (@bmoneke, #877).

- VisaAdapter now closes the manager only when pyvisa-sim is in use (@dkriegner, #900).

- The instrument name definition pattern was harmonized, and the instrument connection argument is now consistently named “adapter” (@bmoneke, #659).

-
Corrects the ProtocolAdapter signature so it uses list properly (@bmoneke, #901)

- Fixes VISAAdapter’s `read_bytes` (@bmoneke, #867)

- Repairs query_delay handling in VISAAdapter (@bmoneke, #765)

- Updates VisaAdapter so the resource manager closes only for pyvisa-sim use (@dkriegner, #900)
