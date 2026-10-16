# Generic types mixins

The [generic_types](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html) module provides mixin classes for shared instrument types. For instance, an instrument that follows SCPI standards can include [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin):

```python
from pymeasure.instruments.instrument import Instrument

from pymeasure.instruments.generic_types import SCPIMixin

class SomeSCPIInstrument(SCPIMixin, Instrument):
    """This instrument has properties and methods defined for all SCPI instruments"""

```

This mixin supplies default SCPI properties such as [`id`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin.id) and [`status`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin.status), plus default methods such as [`clear()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin.clear) and [`reset()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin.reset), to `SomeSCPIInstrument`.

To verify whether your instrument can safely inherit from [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), run `pytest -k scpi_mixin --device-address "<instrument-address>"`.
