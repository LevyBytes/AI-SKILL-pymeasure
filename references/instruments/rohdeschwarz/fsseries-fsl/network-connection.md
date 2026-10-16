# Connect an FSL over the network

After network attachment, read the instrument IP from the front-panel UI: choose “Setup”, then “General Settings” -> “Network Address”.

Use that address in a connection call such as this:

```python
from pymeasure.instruments.rohdeschwarz import FSL
fsl = FSL("TCPIP::192.168.1.123::INSTR")

```
