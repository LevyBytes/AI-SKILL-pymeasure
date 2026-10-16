# pymeasure.instruments.redpitaya.redpitaya_scpi.RedPitayaScpi

*class *pymeasure.instruments.redpitaya.redpitaya_scpi.RedPitayaScpi(*adapter=None*, *ip_address='169.254.134.87'*, *port=5000*, *name='Redpitaya SCPI'*, *read_termination='\\r\\n'*, *write_termination='\\r\\n'*, ***kwargs*)

Bases: [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin), [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Class wrapper for the Redpitaya reconfigurable board.

Connect to the instrument over a TCP/IP Socket adapter written as "TCPIP::x.y.z.k::port::SOCKET". In that string, x.y.z.k is the SCPI server IP address, and port is the TCP/IP port, commonly 5000; the board must already have its SCPI server running.

To start the SCPI server, attach the redpitaya to the computer or network, then open the URL printed on the board's network connector. It should look similar to "RP-F06432.LOCAL/". In the web interface, go to the menu, launch the Development application, and enable the SCPI server; the interface then reports the IP/port address needed by this Instrument.

Parameters:

- **ip_address** (`str`) - IP address used when adapter is None. (default: `'169.254.134.87'`)

- **port** (`int`) - Port number used when adapter is None. (default: `5000`)
