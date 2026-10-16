# pymeasure.display.widgets.log_widget.HTMLFormatter.format

[Owning PyMeasure class, adapter and connection contract](overview.md)

format(*record*)

Convert the given record into text.

The record’s attribute dictionary supplies values for string formatting, producing the returned string. Before that formatting step, the formatter performs some setup: the record message is calculated with LogRecord.getMessage(); when the format requires time, detected through usesTime(), formatTime() formats the event timestamp; and any exception details are processed by formatException() before being added to the message.
