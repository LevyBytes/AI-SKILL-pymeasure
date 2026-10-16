# pymeasure.instruments.agilent.AgilentE5062A.pop_err

[Owning PyMeasure class, adapter and connection contract](overview.md)

pop_err()

Remove and return one error from the error queue. The return value is a tuple with the code and error description. Error code 0 means success.

Clear the Error queue with the standard SCPI `agilentE5062A.clear()` method.
