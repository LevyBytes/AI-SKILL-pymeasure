# pymeasure.instruments.hp.HP8561B.harmonic_number_lock

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *harmonic_number_lock*: Any*

Lock operation to one selected harmonic so sweeping an external frequency band uses no other harmonic. Use the `fullband` command to choose a frequency band; it selects a suitable harmonic for that band. Change the harmonic number with `harmonic_number_lock`. `harmonic_number_lock` also works in internal-mixing modes. After `fullband` or `harmonic_number_lock` is set, entered center frequencies and spans must be inside the frequency band for the active harmonic. Activating `set_full_span` limits the span to the selected harmonic's frequency band.
