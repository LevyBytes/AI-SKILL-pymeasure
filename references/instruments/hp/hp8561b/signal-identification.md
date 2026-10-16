# pymeasure.instruments.hp.HP8561B.signal_identification

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *signal_identification*: Any*

Control signal identification for external mixing frequency bands. Two methods are available. AUTO uses the image response method to find correct mixer responses. Put a marker on the desired signal, then set `signal_identification = 'AUTO'`. A correct response's frequency appears in the active function block. Use AUTO before calling `signal_identification_to_center_frequency()`. The MAN method shifts responses horizontally and vertically. A correct response moves horizontally by less than 80 kHz. For MAN accuracy, keep the frequency span under 20 MHz. True means manual mode is active; False means auto mode is active or `signal_identification` is off.
