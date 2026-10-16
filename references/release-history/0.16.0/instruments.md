# Version 0.16.0 (2026-05-20) — Instruments

- Add Aculight Argos OPO laser system (@BenediktBurger, #1046)

- Agilent 33250A waveform generator support was added (@PeterPirog, #1425).

- Add Agilent B2980 electrometer series (@Falk3579, #1296)

- Add Agilent E5270B (@Falk3579, #1340, #1359, #1365)

- Agilent N8975A noise figure analyzer support was added (@Falk3579, #1397).

- Add FormFactor Velox Waferprobers (@Falk3579, #1385)

- Add Ilxlightwave ldp3811 pulsed current source (@fg-lumentum, #1367)

- Add Keithley 2510 Sourcemeter (@fg-lumentum, #1239, #1333)

- Add Keithley 4200A-SCS (@Falk3579, #1332)

- Keysight 81160A Pulse Function Arbitrary Noise Generator support was added (@ilev-sergey, #1250).

- Add Keysight PNAs (@Falk3579, #1356)

- LakeShore 3xx temperature controller support was added (@DF9AS, #1334).

- Add Oxford Instruments Mercury Intelligent Temperature Controller (@JAW90, #1198)

- Add PTW Diamentor DAP dosemeter (@Falk3579, #1302, #1449)

- Add PTW UNIDOS dosemeters (@Falk3579, #1279, #1442)

- Santec TSL-500 series tunable laser support was added, including TSL-550 and TSL-770 (@fg-lumentum, #1253, #1390).

- Add Siglent oscilloscope SDS1000XHD (@lucasbraud, #1325)

- Add Spellman XRV high voltage power supplies (@Falk3579, #1329, #1440)

- Add SRS LDC500Series (@fg-lumentum, #1278, #1346)

- Add Thorlabs mbx series (@fg-lumentum, #1361)

- Fix Temptronic tests (@ilev-sergey, #1277)

- HP3478A was fixed to request calibration data through `write_binary_values()` (@dl8dtl, #1263).

- Fix docstring in Keithley4200 (@Falk3579, #1339)

- Agilent33220A parameter ranges were corrected (@Patschke, #1342).

- Keithley 2000 `voltage_nplc` and `enable_filter` were fixed (@d-el, @chieh0517, #1360, #1393).

- Fix `read` of Racal 1992 (@BenediktBurger, #1355)

- Older docstrings were converted to the new style (@BenediktBurger, #1247, #1243).

- The Advantest R624X driver now includes sequence builders, hardware-verified corrections, and documentation (@wichers, #1408).

- Update Agilent channels (@BenediktBurger, #1089)

- Agilent 33500 properties were updated, and a SCPI mixin was added (@ilev-sergey, #1245, #1246).

- Agilent 34450 now includes `local()` and protocol tests (@Falk3579, #1427, #1436).

- Agilent 4284A was extended with new correction functionality (@Falk3579, #1304).

- Agilent B1500 gained SPGU and CMU module support plus new documentation (@ilev-sergey, #1380, #1344, #1412).

- The Agilent B1500 SMU class now inherits from `Channel` (@ilev-sergey, #1387).

- Agilent E4408B was updated with SCPIMixin and new docstrings (@BenediktBurger, #1438).

- Agilent E4980A received tests (@Falk3579, #1300).

- Keithley 2400 received a major rework (@fg-lumentum, #1347).

- The Keithley 2450 docstring now notes that buffer handling is not currently supported (@dsimat, #1238).

- Keithley 6221 now supports delta mode (@panasee, #1242).

- Update MS464xB docstrings (@Falk3579, #1352)

- SRS 860 method names were improved (@panasee, #1289).

- Update SRS 860 min ampl (@chieh0517, #1426)

- Yokogawa Aq6370 series updates added sensitivity control, sweep status, connections, and traces (@fg-lumentum, @BenediktBurger, #1138, #1234, #1286, #1354).
