# pymeasure.instruments.hp.HP8561B.set_signal_identification_to_center_frequency

[Owning PyMeasure class, adapter and connection contract](overview.md)

set_signal_identification_to_center_frequency()

Set the center frequency to the frequency returned by SIGID.

For this command to run correctly, SIGID must be in AUTO mode and must have found a valid result. Use SIGID for signals greater than 18 GHz {i.e., in external mixing mode). On an HP 8561B, SIGID and IDCF can also be used with signals less than 6.5 GHz.
