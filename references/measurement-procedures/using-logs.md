# Using Logs

Logs record important procedure-execution details. This section uses the Python logging module with PyMeasure to document what happened during a run and to provide diagnostic information for issues or bugs.

Now add logging to SimpleProcedure.

The complete program is in the [upstream source](https://raw.githubusercontent.com/pymeasure/pymeasure/08c4a91f5255c937a909cc21e70fa3fafd76333e/docs/tutorial/procedure.rst).

The example first imports the Python logging module and obtains a logger with the `__name__` argument, which scopes log messages to the current file. To collect every log message, including those from pymeasure, use the `''` argument instead. The `console_log` function is a convenient way to send log output to the console. The Python logging documentation covers logger usage in more detail.
