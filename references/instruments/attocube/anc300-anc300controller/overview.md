# pymeasure.instruments.attocube.anc300.ANC300Controller

*class *pymeasure.instruments.attocube.anc300.ANC300Controller(*adapter=None*, *name='attocube ANC300 Piezo Controller'*, *axisnames=''*, *passwd=''*, *query_delay=0.05*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Attocube ANC300 Piezo stage controller supporting multiple axes

Parameters:

- **adapter** - VISA resource name for the controller, such as `TCPIP::<address>::<port>::SOCKET`, or an existing Adapter. The instruments default communication port is 7230. (default: `None`)

- **axisnames** - list of axis names used to create properties with matching names (default: `''`)

- **passwd** - password for the attocube standard console (default: `''`)

- **query_delay** - default delay in s between sending and reading (default 0.05) (default: `0.05`)

- **host** –

Instrument host address, for example 169.254.0.1

Deprecated since version 0.11.2: The `host` argument is deprecated; use the `adapter` argument instead.

- **kwargs** - Any valid VISAAdapter key-word argument.
