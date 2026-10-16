# pymeasure.instruments.eurotest.EurotestHPP120256.ask

[Owning PyMeasure class, adapter and connection contract](overview.md)

ask(*command*)

Override the Instrument ask method to include query_delay time in the parent call. :type command: :param command: Command string sent to the instrument. :returns: Device response string without read_termination.
