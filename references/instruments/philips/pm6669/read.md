# pymeasure.instruments.philips.PM6669.read

[Owning PyMeasure class, adapter and connection contract](overview.md)

read()

Read function that includes the instrument bug work around.

When the device receives a request with a measurement ready, it returns both the reply and the measurement. The measurement gets removed from that response and stored in a backlog Queue.
