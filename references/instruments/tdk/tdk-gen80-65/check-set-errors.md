# pymeasure.instruments.tdk.tdk_gen80_65.TDK_Gen80_65.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

Use this command only for setters, meaning commands that are not queries.

For a non-querying command, meaning one without the “?” symbol such as the instrument command “PV 10”, the instrument responds with “OK” for an accepted command or with an error code. That acknowledgement confirms receipt. Querying commands, meaning commands that include the “?” symbol such as “PV?”, return the requested value instead of that acknowledgement.
