# pymeasure.instruments.hp.HP8561B.peak_preselector

[Owning PyMeasure class, adapter and connection contract](overview.md)

peak_preselector()

Peaks the preselector on the HP 8561B Spectrum Analyzer.

Before running PP, verify that the whole frequency span is in high band, put the desired trace in clear-write mode, and place a marker on the desired signal. PP zooms to zero span, peaks preselector tracking, and returns to the original position. Read the updated preselector peaking number with PSDAC. Any commands after PP wait until preselector peaking is complete.
