# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.self_test

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *self_test*: Any*

Query the self-test result (`*TST?`).

Warning

This command can take a long time to finish and is not supported on every model. A VISA timeout error may occur. Consider using a try/except block or raising the adapter timeout before calling it.
