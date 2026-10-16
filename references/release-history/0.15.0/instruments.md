# Version 0.15.0 (2025-01-15) — Instruments

- Add Agilent E5062A (@AlecVercruysse, #1146)

- Add Hewlett Packard 8753E VNA (@Sionwage, #1004)

- Add Keithley DAQ6510 (@Aphelion82, #1128)

- Add Keithley2281S (@PfannenHans, #1054)

- Add LD400P electronic load (@RobertoRoos, #1168)

- Add Philips PM6669 Universal Frequency Counter (@dirkjankrijnders, #570)

- A Rohde&Schwarz FSSeries class was added for instruments such as FSL, formerly a stand-alone class, as well as FSW and related devices (@jnnskls, #1156). The instrument class FSL was previously imported from `pymeasure/instruments/rohdeschwarz/fsl.py`; it is now available from `pymeasure/instruments/rohdeschwarz/fsseries.py` together with the FSSeries base class and FSW.

- Add Rigol dg822 waveform generator (@fthouin, #1159)

- Add Siglent SDS1072CML oscilloscope (@fthouin, #1080, 1195)

- Additional Thyracont vacuum transducer device types were added (@dkriegner, #1143).

- Agilent E5062A was fixed with documentation updates and a rename from active_traces to visible_traces (@AlecVercruysse, #1174).

- AnritsuMS2090A was fixed by confirming SCPIMixin support (@icchalmers, #1191).

- A test-suite race condition caused by HP8116A tests was fixed (@kpet, #1145).

- The description of `Keithley2000.measure_resistance` was corrected (@J3NZ0L, #1193).

- Fix test for Keithley6510 (@BenediktBurger, #1135)

- Fix Kepco BOP power supplies documentation (@JAW90, #1199)

- AFG3152CChannel was updated to match the documentation (@ssimpson-ens, #1176).

- Keysight E3631A now has an `output_enabled` property on individual channels (@inonRAAAM, #1209).

- Teledyne was updated with VBS methods (@RobertoRoos, #1166).
