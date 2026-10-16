# Adding a device address and adding delay

Consider a device whose protocol puts its address in the first three characters and echoes responses in that format. The customization is small: `write()` adds the address before the command, while `read()` removes it and performs validation. The same pattern could attach a checksum. Because the device also needs a pause after receiving a command before it answers, `wait_for()` should always apply a fixed delay.

```python
from pymeasure.instruments.instrument import Instrument

class ExtremeCommunication(Instrument):
    """Control the ExtremeCommunication instrument.

    :param address: The device address for the communication.
    :param query_delay: Wait time after writing and before reading in seconds.
    """
    def __init__(self, adapter, name="ExtremeCommunication", address=0, query_delay=0.1):
        super().__init__(adapter, name)
        self.address = f"{address:03}"
        self.query_delay = query_delay

    def write(self, command):
        """Add the device address in front of every command before sending it."""
        super().write(self.address + command)

    def wait_for(self, query_delay=0):
        """Wait for some time.

        :param query_delay: override the global query_delay.
        """
        super().wait_for(query_delay or self.query_delay)

    def read(self):
        """Read from the device and check the response.

        Assert that the response starts with the device address.
        """
        got = super().read()
        if got.startswith(self.address):
            return got[3:]
        else:
            raise ConnectionError(f"Expected message address '{self.address}', but read '{got[3:]}' for wrong address '{got[:3]}'.")

    voltage = Instrument.measurement(
        ":VOLT:?", """Measure the voltage in Volts.""")

```

With `address=12` at initialization time, requesting voltage sends `"012:VOLT:?"` and the driver should look for a reply that starts with `"012"`.
