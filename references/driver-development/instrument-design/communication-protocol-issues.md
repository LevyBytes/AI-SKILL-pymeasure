# Communication protocol issues

- When an instrument replies to every message, including setting commands, set the setting's `check_set_errors = True` parameter and redefine `check_set_errors()` so it reads the reply; see [`hcp.TC038D`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hcp/tc038d.html#pymeasure.instruments.hcp.TC038D)

- Binary, frame-based communication, see [`hcp.TC038D`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hcp/tc038d.html#pymeasure.instruments.hcp.TC038D)

- For replies that all share the same length, see [`aja.DCXS`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aja/DCXS.html#pymeasure.instruments.aja.DCXS)

- For startup garbage messages that pollute the buffer, see [`aja.DCXS`](https://pymeasure.readthedocs.io/en/latest/api/instruments/aja/DCXS.html#pymeasure.instruments.aja.DCXS)

- When both an instrument and its channel must override values while still using the correct ask method, see [`tcpowerconversion.CXN`](https://pymeasure.readthedocs.io/en/latest/api/instruments/tcpowerconversion/tccxn.html#pymeasure.instruments.tcpowerconversion.CXN)
