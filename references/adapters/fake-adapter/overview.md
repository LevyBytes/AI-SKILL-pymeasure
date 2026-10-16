# pymeasure.adapters.FakeAdapter

*class *pymeasure.adapters.FakeAdapter(*log=None*, ***kwargs*)

Bases: `Adapter`

Supplies a fake debugging adapter that echoes the command, making arbitrary values testing possible.

```python
from pymeasure.adapters.adapter import FakeAdapter

a = FakeAdapter()
assert a.read() == ""
a.write("5")
assert a.read() == "5"
assert a.read() == ""
assert a.ask("10") == "10"
assert a.values("10") == [10]

```
