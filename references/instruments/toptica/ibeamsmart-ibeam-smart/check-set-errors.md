# pymeasure.instruments.toptica.ibeamsmart.IBeamSmart.check_set_errors

[Owning PyMeasure class, adapter and connection contract](overview.md)

check_set_errors()

After getting a property, check for errors and log them.

Verify that the last reply is only ‘[OK]’. Otherwise, raise ValueError and flush the read buffer because communication may be out of sync.
