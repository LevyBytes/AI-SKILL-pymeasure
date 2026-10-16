# pymeasure.instruments.philips.PM6669.read_measurement

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_measurement(*wait_for_srq=False*)

Wait until the device sends an SRQ, then read the result.

With wait_for_srq set, MSR needs to be MSRFlag.MEASUREMENT_READY.
