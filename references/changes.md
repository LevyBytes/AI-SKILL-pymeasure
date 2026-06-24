# Changes (part 1)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### Changelog

### Upcoming release

### Removed

-

GUI packages are no longer part of the default dependency set. To include the GUI extras, install PyMeasure with `pip install pymeasure[gui]`; Conda installations continue to include every dependency.

-

The deprecated `control` arguments `command_process` and `kwargs` have been removed.

-

For Toptica Ibeamsmart, the deprecated methods `laser_enabled`, `channel1_enabled`, and `channel2_enabled` were removed; use `emission` together with the driver channels.

### Deprecated

-

The behavior that silently returns str from `values` and property creators such as `control` when casting fails is now deprecated. Use an explicit helper, for example `cast_or_str(float)`, for that case.

-

Toptica Ibeamsmart `enable_continous` is deprecated; replace it with `enable_continuous`.

-

Thermotron 3800 `initalize_oven` is deprecated; use `initialize_oven` instead.

### Version 0.16.0 (2026-05-20)

Primary changes in this release:

-

Add support for Python 3.13

-

The policy now permits type hints, which have already been introduced in the instruments core.

-

25 new instruments

-

`Instrument.control` now applies `get_process` only to a single returned value, not to returned lists. Use the `get_process_list` parameter when a list of values needs processing.

-

The Keithley 2400 implementation was improved and includes some behavioral changes. The previous implementation remains available as `Keithley2400Legacy`.

### Removed

-

Remove support for Python 3.8

-

Deprecated Adapter and Instrument parameters `preprocess_reply` and `query_delay` were removed.

-

Deprecated Adapter methods `ask`, `values`, and `binary_values` were removed.

-

The deprecated Telnet and VXI adapters were removed.

### Deprecated

-

In `pymeasure/instruments/srs/SR860.py`, the `sensitvity` attribute was replaced with `sensitivity`.

-

In `pymeasure/instruments/srs/SR860.py`, the `filer_synchronous` attribute was replaced with `filter_synchronous`.

-

In `pymeasure/instruments/advantest/advantestR624X.py`, the `query_operation_mode` method was replaced by the `operation_mode` property.

-

In `pymeasure/instruments/advantest/advantestR624X.py`, the `query_system_settings` method was replaced by the `system_settings` property.

-

In `pymeasure/instruments/advantest/advantestR624X.py`, `interrupt_sequence_command` was replaced with `interrupt_sequence`.

-

In `pymeasure/instruments/advantest/advantestR624X.py`, `sequence_program_listing` was replaced with `query_sequence_program`.

-

In `pymeasure/instruments/advantest/advantestR624X.py`, `digital_out_enable_data` was replaced with `digital_output_enable`.

-

In `pymeasure/instruments/advantest/advantestR624X.py`, the `query_output_waveform` method was replaced by the `output_waveform_settings` property.

-

In `pymeasure/instruments/advantest/advantestR624X.py`, the `query_measurement_settings` method was replaced by the `measurement_range_settings` property.

-

In `pymeasure/instruments/advantest/advantestR624X.py`, the `query_response_settings` method was replaced by the `response_settings` property.

-

In `pymeasure/instruments/advantest/advantestR624X.py`, the `query_data_output_settings` method was replaced by the `data_output_settings` property.

-

In `pymeasure/instruments/advantest/advantestR624X.py`, the `query_io_settings` method was replaced by the `io_settings` property.

-

In `pymeasure/instruments/advantest/advantestR624X.py`, `calibration_init` was replaced with `init_calibration`.

-

In `pymeasure/instruments/advantest/advantestR624X.py`, `calibration_store_factor` was replaced with `store_calibration_factor`.

### Instruments

-

Add Aculight Argos OPO laser system (@BenediktBurger, #1046)

-

Agilent 33250A waveform generator support was added (@PeterPirog, #1425).

-

Add Agilent B2980 electrometer series (@Falk3579, #1296)

-

Add Agilent E5270B (@Falk3579, #1340, #1359, #1365)

-

Agilent N8975A noise figure analyzer support was added (@Falk3579, #1397).

-

Add FormFactor Velox Waferprobers (@Falk3579, #1385)

-

Add Ilxlightwave ldp3811 pulsed current source (@fg-lumentum, #1367)

-

Add Keithley 2510 Sourcemeter (@fg-lumentum, #1239, #1333)

-

Add Keithley 4200A-SCS (@Falk3579, #1332)

-

Keysight 81160A Pulse Function Arbitrary Noise Generator support was added (@ilev-sergey, #1250).

-

Add Keysight PNAs (@Falk3579, #1356)

-

LakeShore 3xx temperature controller support was added (@DF9AS, #1334).

-

Add Oxford Instruments Mercury Intelligent Temperature Controller (@JAW90, #1198)

-

Add PTW Diamentor DAP dosemeter (@Falk3579, #1302, #1449)

-

Add PTW UNIDOS dosemeters (@Falk3579, #1279, #1442)

-

Santec TSL-500 series tunable laser support was added, including TSL-550 and TSL-770 (@fg-lumentum, #1253, #1390).

-

Add Siglent oscilloscope SDS1000XHD (@lucasbraud, #1325)

-

Add Spellman XRV high voltage power supplies (@Falk3579, #1329, #1440)

-

Add SRS LDC500Series (@fg-lumentum, #1278, #1346)

-

Add Thorlabs mbx series (@fg-lumentum, #1361)

-

Fix Temptronic tests (@ilev-sergey, #1277)

-

HP3478A was fixed to request calibration data through `write_binary_values()` (@dl8dtl, #1263).

-

Fix docstring in Keithley4200 (@Falk3579, #1339)

-

Agilent33220A parameter ranges were corrected (@Patschke, #1342).

-

Keithley 2000 `voltage_nplc` and `enable_filter` were fixed (@d-el, @chieh0517, #1360, #1393).

-

Fix `read` of Racal 1992 (@BenediktBurger, #1355)

-

Older docstrings were converted to the new style (@BenediktBurger, #1247, #1243).

-

The Advantest R624X driver now includes sequence builders, hardware-verified corrections, and documentation (@wichers, #1408).

-

Update Agilent channels (@BenediktBurger, #1089)

-

Agilent 33500 properties were updated, and a SCPI mixin was added (@ilev-sergey, #1245, #1246).

-

Agilent 34450 now includes `local()` and protocol tests (@Falk3579, #1427, #1436).

-

Agilent 4284A was extended with new correction functionality (@Falk3579, #1304).

-

Agilent B1500 gained SPGU and CMU module support plus new documentation (@ilev-sergey, #1380, #1344, #1412).

-

The Agilent B1500 SMU class now inherits from `Channel` (@ilev-sergey, #1387).

-

Agilent E4408B was updated with SCPIMixin and new docstrings (@BenediktBurger, #1438).

-

Agilent E4980A received tests (@Falk3579, #1300).

-

Keithley 2400 received a major rework (@fg-lumentum, #1347).

-

The Keithley 2450 docstring now notes that buffer handling is not currently supported (@dsimat, #1238).

-

Keithley 6221 now supports delta mode (@panasee, #1242).

-

Update MS464xB docstrings (@Falk3579, #1352)

-

SRS 860 method names were improved (@panasee, #1289).

-

Update SRS 860 min ampl (@chieh0517, #1426)

-

Yokogawa Aq6370 series updates added sensitivity control, sweep status, connections, and traces (@fg-lumentum, @BenediktBurger, #1138, #1234, #1286, #1354).

### Instruments mechanics

-

Prologix adapter support now includes `_write_bytes()` and `_read_bytes()` (@dl8dtl, #1259).

-

`list_resources()` now handles SerialException (@hvegh, #1287).

-

`get_process_list` was added and made dynamic (@BenediktBurger, @Falk3579, #1291, #1313, #1315).

-

Typing was added to `expected_protocol`, adapters, and `Instrument` (@BenediktBurger, #1084, #1331).

-

Property creator docstring lists now include a concrete hint (@BenediktBurger, #1281).

-

A SCPI mixin test was added for devices (@fg-lumentum, #1391).

-

Update Prologix documentation (@dl8dtl, #1272)

### Automation

-

The qtpy dependency was added for Qt version shimming (@Benbriel, #1285).

-

Add `description` to `Parameters` (@Benbriel, #1211)

-

Procedures now emit results in batches (@jvdoorn, #1256).

-

Numeric constants were replaced with the corresponding Qt enum values (@dl8dtl, #1265).

-

Removed `np.fromstring(sep="")` usage was replaced with `np.frombuffer` (@BenediktBurger, #1330).

-

BooleanParameter now accepts numpy.bool (@Falk3579, #1373).

-

Workers now check should_stop after `startup()` before execute() runs (@breakU1, #1445).

-

Add vector parameter input (@Falk3579, #1376, #1377, #1382)

-

`load_module()` was replaced by `exec_module()` (@Falk3579, #1415).

-

`Results.data` now checks file size and skips reading when the data file has not changed (@mcdo0486, #1429).

### GUI

-

Add a console widget (@breakU1, #1431)

-

The custom_ui and image_gui examples were updated (@CasperSchippers, @Falk3579, #1266, #1337).

-

The managed window now supports multi-selection when deleting and removing experiments (@breakU1, #1451).

-

Example units for `Ohm` were corrected (@Falk3579, #1338).

### Documentation

-

Update documentation regarding type hints (@BenediktBurger, #1324)

-

Add sphinx-autodoc-typehints extension (@ilev-sergey, #1406)

-

An AGENTS.md file was added for AI coding agents (@BenediktBurger, #1372).

-

Read the Docs was updated to Ubuntu 24.04 (@cjermain, #1419).

-

Fix documentation typos (@ilev-sergey, #1249)

### Miscellaneous

-

The documentation now lists related projects (@BenediktBurger, #1335).

-

uv.lock was added to gitignore (@maederan201, #1453).

-

Add Python 3.13 support. (@BenediktBurger, #1173)

-

Add dependapot configuration (@BenediktBurger, #1307)

-

Remove deprecated parts (@BenediktBurger, #1268)

-

Remove support for Python 3.8 (@BenediktBurger, #1317)

-

Update copyright (@ilev-sergey, @Falk3579, #1248, #1402, #1414)

-

The pandas dependency constraint was updated to <4 (@maduka-ariyasiri, #1424).

-

Bump CI actions versions (@dependabot, #1327, #1328, #1351, #1353, #1386, #1417, #1418, #1408)

-

Fix ruff configuration (@ilev-sergey, #1236)

-

Fix formatting (@Falk3579, #1267, #1269, #1316, #1375)

-

Raised errors now show the full stack trace (@BenediktBurger, #1270).

-

Fix failing CI (@CasperSchippers, #1454)

### New Contributors

Contributors in this release group include @ilev-sergey, @Benbriel, @fg-lumentum, @dsimat, @panasee, and @jvdoorn.
Additional contributor handles are @dl8dtl, @Falk3579, @hvegh, @dependabot[bot], @DF9AS, and @Patschke.
The list also includes @d-el, @lucasbraud, @chieh0517, @breakU1, @PeterPirog, and @maduka-ariyasiri.

**Full Changelog**: [https://github.com/pymeasure/pymeasure/compare/v0.15.0…v0.16.0](https://github.com/pymeasure/pymeasure/compare/v0.15.0...v0.16.0)

### Version 0.15.0 (2025-01-15)

Primary changes in this release:

-

pyproject.toml replaces setup.cfg

-

12 new instruments

### Deprecated features

-

The FSL class imported from `pymeasure/instruments/rohdeschwarz/fsl.py` is deprecated. The current implementation lives in `pymeasure/instruments/rohdeschwarz/fsseries.py`.

### Instruments

-

Add Agilent E5062A (@AlecVercruysse, #1146)

-

Add Hewlett Packard 8753E VNA (@Sionwage, #1004)

-

Add Keithley DAQ6510 (@Aphelion82, #1128)

-

Add Keithley2281S (@PfannenHans, #1054)

-

Add LD400P electronic load (@RobertoRoos, #1168)

-

Add Philips PM6669 Universal Frequency Counter (@dirkjankrijnders, #570)

-

A Rohde&Schwarz FSSeries class was added for instruments such as FSL, formerly a stand-alone class, as well as FSW and related devices (@jnnskls, #1156). The instrument class FSL was previously imported from `pymeasure/instruments/rohdeschwarz/fsl.py`; it is now available from `pymeasure/instruments/rohdeschwarz/fsseries.py` together with the FSSeries base class and FSW.

-

Add Rigol dg822 waveform generator (@fthouin, #1159)

-

Add Siglent SDS1072CML oscilloscope (@fthouin, #1080, 1195)

-

Additional Thyracont vacuum transducer device types were added (@dkriegner, #1143).

-

Agilent E5062A was fixed with documentation updates and a rename from active_traces to visible_traces (@AlecVercruysse, #1174).

-

AnritsuMS2090A was fixed by confirming SCPIMixin support (@icchalmers, #1191).

-

A test-suite race condition caused by HP8116A tests was fixed (@kpet, #1145).

-

The description of `Keithley2000.measure_resistance` was corrected (@J3NZ0L, #1193).

-

Fix test for Keithley6510 (@BenediktBurger, #1135)

-

Fix Kepco BOP power supplies documentation (@JAW90, #1199)

-

AFG3152CChannel was updated to match the documentation (@ssimpson-ens, #1176).

-

Keysight E3631A now has an `output_enabled` property on individual channels (@inonRAAAM, #1209).

-

Teledyne was updated with VBS methods (@RobertoRoos, #1166).

### Automation

-

File reads and writes now explicitly use utf8 encoding, enabling special characters in stored data. Earlier releases did not set the encoding explicitly, which may affect loading older data files; when needed, the encoding can be changed, for example by monkey-patching the `pymeasure.experiment.Results.ENCODING` property. (@CasperSchippers, #1123)

-

Procedure gained a `has_next` method (@Did-Mas, #1185).

-

Logging changed from the root logger to a module-specific logger (@mmerlo, #1165).

### Documentation

-

Several typos in procedure.rst were corrected (@kpet, #1141).

-

contribute.rst was updated with GitHub Desktop coverage as well (@bernhardlang, @OrionSmedley, #983, #1171).

-

Fix documentation errors (@msmttchr, @kpet, #1133, #1148)

-

Update InstrumentKit reference (@emmanuel-ferdman, #1187)

-

Change copyright year to 2025 (@BenediktBurger, #1210)

### Miscellaneous

-

Prepare for v0.14.0 (@BenediktBurger, #1104)

-

The browser item context menu gained “Reveal in File Explorer” (@Did-Mas, #1188).

-

Update numpy 2 test (@CasperSchippers, #1126)

-

An install group for documentation builds was added (@RobertoRoos, #1180).

-

setup.cfg was removed and replaced by pyproject.toml (@RobertoRoos, #1182).

### New Contributors

@Sionwage, @bernhardlang, @Aphelion82, @kpet, @mmerlo, @OrionSmedley, @ssimpson-ens, @Did-Mas, @emmanuel-ferdman, @icchalmers, @fthouin, @PfannenHans, @dirkjankrijnders, @J3NZ0L, @inonRAAAM,

**Full Changelog**: [https://github.com/pymeasure/pymeasure/compare/v0.14.0…v0.15.0](https://github.com/pymeasure/pymeasure/compare/v0.14.0...v0.15.0)

### Version 0.14.0 (2024-05-22)

Primary changes in this release:

-

Add support for numpy 2.0

-

Add support for python 3.12

-

Academic citation support was improved with a current Zenodo DOI and citation metadata.

-

A default `queue` method and `FileInputWidget` were added, making it faster to start using the PyMeasure interface (`ManagedWindow`).

-

A `SCPIMixin` base class was added for instruments, replacing the pattern of defining `includeSCPI=True`.

-

Instrument manufacturer modules are no longer imported from `pymeasure/instruments/__init__.py`. Previously, importing one instrument inside a procedure loaded every instrument into memory through the manufacturer modules referenced by `pymeasure/instruments/__init__.py`. Removing those imports lowers PyMeasure memory use when a single instrument is imported. Instrument classes now need imports from the manufacturer module or directly from the driver file. For example, change `from pymeasure.instruments import Extreme5000` to `from pymeasure.instruments.extreme import Extreme5000` or `from pymeasure.instruments.extreme.extreme5000 import Extreme5000`.

-

17 new instruments

### Deprecated features

-

`TelnetAdapter` was removed because its library is deprecated (@BenediktBurger, #1045).

-

`ManagedWindowBase` now uses `enable_file_input` instead of the `directory_input` keyword argument (@CasperSchippers, #964).

-

All instruments must now provide the `includeSCPI` parameter, including instruments that use SCPI (@BenediktBurger, #1007).

-

Using includeSCPI=True is deprecated; devices with SCPI command support should inherit from `SCPIMixin`.

-

`LakeShoreTemperatureChannel` now uses `celsius` instead of the `celcius` attribute (@afuetterer, #1003).

-

For Keithley instruments, the `error` property was replaced with `next_error`.

-

Pendulum CNT-91 now uses `gate_time` instead of the `measurement_time` property.

-

For Pendulum CNT-91, the `buffer_frequency_time_series` keyword argument `sample_rate` was replaced with `gate_time`.

-

MKS937B `unit` now uses `instruments/mksinst/mks937b/Unit` rather than strings (@dkriegner, @BenediktBurger #1034).

### Instruments mechanics

-

A SCPI base class, `SCPIMixin`, was added to replace `includeSCPI=True` (@BenediktBurger, #905, #1007, #1019, #1047).

-

SCPI instruments now include the `next_error` property (@BenediktBurger, #1024).

-

`wait_for` now defaults to `query_delay=None` (@BenediktBurger, #1077).

-

The default empty dictionary used by `expected_protocol` was fixed (@BenediktBurger, #1087).

-

Automatic importing of every instrument from `pymeasure/instruments/__init__.py`` was removed (@mcdo0486, #919).

-

`find_serial_port` was added to locate a serial port from USB information (@BenediktBurger, #982).

### Instruments

-

Add Agilent4294A (@driftregion, #998)

-

Add Agilent 4284A by (@ConnorGCarr #1079)

-

Add AimTTI PL series power supplies (@guuskuiper, #942)

-

HP11713A Switch & Attenuator Driver support was added (@neuschs, #970).

-

Add HP437B power meter (@neuschs, #979)

-

Add Inficon SQM160 SQM-160 multi-film rate/thickness monitor (@dkriegner, #991)

-

Add Keithley 2182 (@ConnorGCarr, #1043)

-

Add KeithleyDMM6500 (@fwutw, #963)

-

Add Kepco BOP 36-12 Bipolar Power Supply (@JAW90, #1086)

-

Add KeysightE3631A (@OptimisticBeliever, #990)

-

Kuhne Electronic KU SG 2.45 250A microwave generator support was added (@jurajjasik, @BenediktBurger, @1108).

-

Add MKS 974B vacuum pressure transducer (@dkriegner, #1034)

-

Add Proterial rod4 (@ConnorGCarr, #1044)

-

Add Racal-Dana 1992 universal counter (@tomverbeure, #798, #1012)

-

Add redpitaya board (@seb5g, #1010, #1035)

-

Add Teledyne HDO6xxx (@RobertoRoos, #868)

-

Add Yokogawa AQ6370D Optical Spectral Analyzer (@jnnskls, #1059)

-

Property docstrings were fixed across several instruments (@BenediktBurger, #1018).

-

hcp TC038D test checksums were corrected (@BenediktBurger, #987).

-

Fix Hp8116a (@BenediktBurger, #1088)

-

Hp856x now appends amplitude units correctly (@neuschs, #977).

-

Keysight E36312A was fixed after confirmed SCPI functionality (@Konradrundfunk, #1107).

-

Fix Stanford Research SR830 output conversion (@dkriegner, #1069)

-

Fix SR830 missing get_buffer method (@seb5g, #999)

-

The SR860 aux output set command was fixed (@wehlgrundspitze, #1048).

-

The Temptronic test now uses ns perf counter (@BenediktBurger, #1109, #1110).

-

Fix Toptica Ibeamsmart referencing removed adapter function (@BenediktBurger, #1065)

-

Typos in Keithley instrument docstrings were fixed (@V0XNIHILI, #1071).

-

Documentation pages for Keysight, Agilent, and HP were linked (@BenediktBurger, #1021).

-

Agilent33500 Series was updated from `.ch[]` to `.channels[]` (@AlecVercruysse, #945).

-

The AWG401x driver now uses ‘channels’ (@mcdo0486, #944).

-

HP33120A was updated with new burst modulation parameters (@mzen228, #1056).

-

HP34401A was updated with a new remote control command (@Rybok, #992).

-

Update Keithleys’ next_error (@msmttchr, #1030)

-

Update pendulum CNT-91 (@bleykauf, #988)

### GUI

-

A `FileInputWidget` was added so users can choose whether and where experiment data is stored (@CasperSchippers, #964).

-

A default `Queue` method is now implemented for `ManagedWindowBase` (@CasperSchippers, #964).

-

`ScientificInput` was fixed for locale compatibility (@pyZerrenner, #1074).

-

Loading a result file with an empty parameter no longer raises an exception (@poje42, #1016).

### Miscellaneous

-

Add support for python 3.12 (@BenediktBurger, #1051)

-

Add support for numpy 2.0 (@CasperSchippers, #1026)

-

codecov was added to CI and to the readme (@BenediktBurger, #1037, #1052, #1099).

-

A citation file was added for the PyMeasure repository (@mcdo0486, #1092).

-

Add release CI (@BenediktBurger, #1039)

-

The readme now includes a permanent Zenodo DOI (@BenediktBurger, #1095).

-

CI dependencies were bumped to pyvisa 1.13.0 and [checkout@v4](mailto:checkout%40v4) (@mcdo0486, #1097).

-

Fix/pandas futurewarning (@CasperSchippers, #1062)

-

Change copyright year. (@BenediktBurger, #1032)

-

Fix typos (@afuetterer, #1003)

### New Contributors

@guuskuiper, @OptimisticBeliever, @fwutw, @afuetterer, @poje42, @Rybok, @AlecVercruysse, @ConnorGCarr, @mzen228, @jnnskls, @V0XNIHILI, @pyZerrenner, @JAW90, @driftregion, @jurajjasik, @Konradrundfunk

**Full Changelog**: [https://github.com/pymeasure/pymeasure/compare/v0.13.1…v0.14.0](https://github.com/pymeasure/pymeasure/compare/v0.13.1...v0.14.0)

### Version 0.13.1 (2023-10-05)

This release fixes an ineffective Python version restriction in project metadata; only Python<=3.7 environments installing with pip were affected.

### Version 0.13.0 (2023-09-23)

Primary changes in this release:

-

Python 3.7 support was dropped, and Python 3.11 support was added.

-

A test generator was added that observes real-device communication and writes matching protocol tests.

-

2 new instrument drivers have been added.

### Deprecated features

-

Attocube ANC300 deprecates the `stepu` and `stepd` properties; use the new `move_raw` method instead (@dkriegner, #938).

### Instruments

-

Adds a test generator (@bmoneke, #882)

-

Adds Thyracont Smartline v2 vacuum sensor transmitter (@bmoneke, #940)

-

Adds Thyracont Smartline v1 vacuum gauge (@dkriegner, #937)

-

AddsTeledyne base classes with most `LeCroyT3DSO1204` behavior were introduced (@RobertoRoos, #951).

-

Fixes instrument documentation (@mcdo0486, #941, #903, @omahs, #960)

-

Fixes Toptica Ibeamsmart’s __init__ (@waveman68, #959)

-

Fixes VISAAdapter flush_read_buffer() (@ileu, #968)

-

Keithley2306 and AFG3152C were updated to Channels (@bilderbuchi, #953).

### GUI

-

Adds console mode (@msmttchr, #500)

-

Fixes Dock widget (@msmttchr, #961)

### Miscellaneous

-

CI was changed from conda to mamba (@bmoneke, #947).

-

Add support for python 3.11 (@CasperSchippers, #896)

### New Contributors

@waveman68, @omahs, @ileu

**Full Changelog**: [https://github.com/pymeasure/pymeasure/compare/v0.12.0…v0.13.0](https://github.com/pymeasure/pymeasure/compare/v0.12.0...v0.13.0)

### Version 0.12.0 (2023-07-05)

Primary changes in this release:

-

A `Channel` base class was added to simplify implementing instruments that have channels.

-

19 new instrument drivers have been added.

-

Tests were added for common behavior shared by instruments.

-

API cleanup continues in preparation for a future version 1.0. The related deprecations and removals appear below.

### Deprecated features

-

For HP 34401A, the `voltage_ac`, `current_dc`, `current_ac`, `resistance`, and `resistance_4w` properties should be replaced by `function_` and `reading`.

-

For Toptica IBeamSmart, replace `channel1_enabled` with the `ch_1.enabled` property, with the same pattern for channel2. `laser_enabled` is also deprecated; use `emission` instead (@bmoneke, #819).

-

For TelnetAdapter, use `VISAAdapter` instead because VISA supports TCPIP connections. Connect to a server with resource_name `TCPIP[board]::<hostname>::<port>::SOCKET` (@Max-Herbold, #835).

-

For Attocube ANC300, replace the `host` argument by passing a resource string or adapter as `Adapter` to `Instrument`. Communication now uses `VISAAdapter` instead of deprecated `TelnetAdapter`. The initializer accepts `name` as its second keyword argument, so earlier positional initialization arguments such as axisnames, passwd, and query_delay should become keyword arguments.

-

The property creators `control`, `measurement`, and `setting` no longer accept arbitrary keyword arguments. Use `v_kwargs` for arguments that should be forwarded to the `values` method.

-

The property creators `control`, `measurement`, and `setting` no longer accept command_process. Use either a dynamic property or a Channel, depending on the case (@bmoneke, #878).

-

See also the next section.

### New adapter and instrument mechanics

-

Every instrument constructor must accept a `name` argument.

-

Changed: by default, Adapter `read_bytes` no longer stops at a termination character unless `break_on_termchar` is True.

-

The Channel class was added. `Instrument.channels` and `Instrument.ch_X`, where `X` is any channel name, are reserved for channel mechanics.

-

The `check_get_errors` and `check_set_errors` parameters enable calls to same-named methods, making it easier to handle instruments that acknowledge each “set” command.

-

The Channel feature was added to instruments (@bmoneke, mcdo0486, #718, #761, #852, #931).

-

The `values` method gained a `maxsplit` parameter (@bmoneke, #793).

-

A deprecated global preprocess reply path was added for backward compatibility (@bmoneke, #876).

-

VISAAdapter gained a fallback version for discarding the read buffer (@dkriegner, #836).

-

SerialAdapter gained `flush_read_buffer` (@RobertoRoos, #865).

-

PrologixAdapter gained `gpib_read_timeout` (@neuschs, #927).

-

A command-line option was added to pass a resource address for instrument tests (@bleykauf, #789).

-

Testing support now includes “find all instruments” plus channels (@bmoneke, #909, @mcdo0486, #911, #912).

-

A test now confirms that an instrument passes kwargs to its adapter (@bmoneke, #814).

-

Adds property docstring check (@bmoneke, #895)

-

Improves property factories’ docstrings (@bmoneke, #843)

-

Property factories were improved so undefined kwargs are rejected (@bmoneke, #856).

-

Property factories were improved with check_set/get_errors support for invoking same-named methods (@bmoneke, #883).

-

Adapter `read_bytes` was improved (@bmoneke, #839).

-

ProtocolAdapter was improved with a mock connection (@bmoneke, #782), and protocols can now contain empty messages (@bmoneke, #818).

-

Prologix adapter documentation was improved (@bmoneke, #813), and configurable settings were added (@bmoneke, #845).

-

`SerialAdapter` behavior for `read_bytes(-1)` was improved (@RobertoRoos, #866).

-

All instruments were improved with the name kwarg (@bmoneke, #877).

-

VisaAdapter now closes the manager only when pyvisa-sim is in use (@dkriegner, #900).

-

The instrument name definition pattern was harmonized, and the instrument connection argument is now consistently named “adapter” (@bmoneke, #659).

-
