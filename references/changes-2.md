# Changes (part 2)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

Corrects the ProtocolAdapter signature so it uses list properly (@bmoneke, #901)

-

Fixes VISAAdapter’s `read_bytes` (@bmoneke, #867)

-

Repairs query_delay handling in VISAAdapter (@bmoneke, #765)

-

Updates VisaAdapter so the resource manager closes only for pyvisa-sim use (@dkriegner, #900)

### Instruments

-

New Advantest R624X DC Voltage/Current Sources/Monitors (@wichers, #802)

-

New AJA International DC sputtering power supply (@dkriegner, #778)

-

New Anritus MS2090A (@aruznieto, #787)

-

New Anritsu MS4644B (@CasperSchippers, #827)

-

Introduces the DSP 7225 and DSPBase instrument support (@mcdo0486, #902)

-

Adds support for the HP 8560A / 8561B Spectrum Analyzer (@neuschs, #888)

-

New IPG Photonics YAR Amplifier series (@bmoneke, #851)

-

Adds the Keysight E36312A power supply driver (@scandey, #785)

-

New Keithley 2200 power supply (@ashokbruno, #806)

-

New Lake Shore 211 Temperature Monitor (@mcdo0486, #889)

-

Introduces Lake Shore 224 support and refines Lakeshore instruments (@samcondon4, #870)

-

New MKS Instruments 937B vacuum gauge controller (@dkriegner, @bilderbuchi, #637, #772, #936)

-

New Novanta FPU60 laser power supply unit (@bmoneke, #885)

-

Adds TDK Lambda Genesys 80-65 DC and 40-38 DC power supplies (@mcdo0486, 906)

-

New Teledyne T3AFG waveform generator instrument (@scandey, #791)

-

New Teledyne (LeCroy) T3DSO1204 Oscilloscope (@LastStartDust, #697, @bilderbuchi, #770)

-

New T&C Power Conversion RF power supply (@dkriegner, #800)

-

New Velleman K8090 relay device (@RobertoRoos, #859)

-

Enhances Agilent 33500 through the new channel feature (@JCarl-OS, #763, #773)

-

Extends HP 3478A with calibration data helper functions (@tomverbeure, #777)

-

Improves HP 34401A (@CodingMarco, #810)

-

Enhances the Oxford instruments with the new channel feature (@bmoneke, #844)

-

Extends Siglent SPDxxxxX through the new channel feature (@AidenDawn 758)

-

Improves Teledyne T3DSO1204 device tests (@LastStarDust, #841)

-

Fixes Ametek DSP 7270 lockin amplifier issues (@seb5g, #897)

-

Corrects DSP 7265 behavior that wrongly used preprocess_reply (@mcdo0486, #873)

-

Removes the bad print statement in DSPBase.sensitivity (@mcdo0486, #915)

-

Fixes Fluke bath commands (@bmoneke, #874)

-

Corrects a frequency cap issue in HP 8657B (@LongnoseRob, #769)

-

Fixes Keithley 2600 channel calling parent’s shutdown (@mcdo0486, #795)

### Automation

-

Allows result files to open even when parameters are missing (@msmttchr, #780)

-

Checks DATA_COLUMNS entries earlier so active procedures avoid runtime exceptions (@mcdo0486, #796, #934)

### GUI

-

Adds docking windows (@mcdo0486, #722, #762)

-

Adds plot-setting persistence alongside the dock layout save path (@mcdo0486, #850)

-

Adds log widget colouring plus a formatting option (@CasperSchippers, #890)

-

Adds table widget (@msmttchr, #771)

-

Introduces a sequencer architecture that separates it from the graphical tree and prepares later expansion (@msmttchr, #518)

-

Relocates the coordinates label onto the pyqtgraph PlotItem (@CasperSchippers, #822)

-

Fixes ImageWidget crashes when a new measurement starts (@CasperSchippers, #790)

-

Restores checkbox behavior for groups inside inputs-widget (@CasperSchippers, #794)

### Miscellaneous

-

Adds collected solutions for difficult instrument implementation cases (@bmoneke, #853, #861)

-

Refreshes Tutorials/Making_a_measurement/ example_codes (@sansanda, #749)

### New Contributors

@JCarl-OS, @aruznieto, @scandey, @tomverbeure, @wichers, @Max-Herbold, @RobertoRoos

**Full Changelog**: [https://github.com/pymeasure/pymeasure/compare/v0.11.1…v0.12.0](https://github.com/pymeasure/pymeasure/compare/v0.11.1...v0.12.0)

### Version 0.11.1 (2022-12-31)

### Adapter and instrument mechanics

-

Repairs PrologixAdapter.gpib. A VISAAdapter bug previously blocked creating another adapter for the same connection (#765).

**Full Changelog**: [https://github.com/pymeasure/pymeasure/compare/v0.11.0…v0.11.1](https://github.com/pymeasure/pymeasure/compare/v0.11.0...v0.11.1)

### Dependency updates

-

Raises the required [PyQtGraph](https://www.pyqtgraph.org/) version from `pyqtgraph >= 0.9.10` to `pyqtgraph >= 0.12` for the newer PyMeasure display widgets.

### GUI

-

Adds [ManagedDockWindow](https://pymeasure.readthedocs.io/en/latest/tutorial/graphical.html#using-the-manageddockwindow) so applications can host several dockable plots (@mcdo0486, @CasperSchippers, #722)

-

Moves the coordinates label onto the pyqtgraph PlotItem (@CasperSchippers, #822)

-

New sequencer architecture (@msmttchr, @CasperSchippers, @mcdo0486, #518)

-

Adds "Save Dock Layout" support to the DockWidget context menu. (@mcdo0486, #762)

### Version 0.11.0 (2022-11-19)

Primary highlights in this release:

-

11 new instrument drivers have been added

-

Adds a way to test instrument communication **without** connected hardware; see the [protocol-tests documentation](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments.html#protocol-tests).

-

Refines the split between `Instrument` and `Adapter` to simplify future changes. Adapters handle hardware communication, while the communication *protocol* belongs in Instruments. A later section gives the details.

-

Makes the GUI work with Qt6.

-

Begins API cleanup for a later version 1.0. Deprecated items and their eventual removals will be called out clearly in the changelog.

### Deprecated features

For the stable 1.0 path and a more uniform API, several features are now formally deprecated. Using them should emit warnings.

-

Deprecates Adapter methods `ask`, `values`, `binary_values`; call the matching `Instrument` methods instead.

-

Adapter parameter `preprocess_reply`, override `Instrument.read` instead.

-

Replaces `Adapter.query_delay` with `Instrument.wait_for()`.

-

For Keithley 2260B, deprecates the `enabled` property in favor of `output_enabled`.

### New adapter and instrument mechanics

-

User-facing behavior should stay the same; this section mostly matters to instrument implementors.

-

Documents the details under 'Advanced communication protocols' in 'Adding instruments'.

-

Makes Adapter log both written and read messages.

-

Leaves real communication work to specific adapters such as VISAAdapter.

-

`Instrument.control` getter calls `Instrument.values`.

-

Routes `Instrument.values` through `Instrument.ask`, then through `Instrument.write`, `wait_for`, and `read`.

-

Implements instrument-specific protocol quirks by overriding `Instrument.write` and `read`.

-

Uses `Instrument.wait_until_read` for the pause between writing and reading.

-

Keeps binary value reads and writes in the `Adapter` class itself.

-

Bases `PrologixAdapter` on `VISAAdapter` now.

-

Brings `SerialAdapter` closer to `VISAAdapter`: `read`/`write` work with strings, while `read/write_bytes` work with bytes. - Adds termination character support.

### Instruments

-

New Active Technologies AWG-401x (@garzetti, #649)

-

New Eurotest hpp_120_256_ieee (@sansanda, #701)

-

New HC Photonics crystal ovens TC038, TC038D (@bmoneke, #621, #706)

-

Adds HP 6632A/6633A/6634A power supplies (@LongnoseRob, #651)

-

New HP 8657B RF signal generator (@LongnoseRob, #732)

-

New Rohde&Schwarz HMP4040 power supply. (@bleykauf, #582)

-

New Siglent SPDxxxxX series Power Supplies (@AidenDawn, #719)

-

New Temptronic Thermostream devices (@mroeleke, #368)

-

New TEXIO PSW-360L30 Power Supply (@LastStarDust, #698)

-

New Thermostream ECO-560 (@AidenDawn, #679)

-

New Thermotron 3800 Oven (@jcarbelbide, #606)

-

Harmonize instruments’ adapter argument (@bmoneke, #674)

-

Standardizes use of the `shutdown` method (@LongnoseRob, #739)

-

Rework Adapter structure (@bmoneke, #660)

-

Add Protocol tests without hardware present (@bilderbuchi, #634, @bmoneke, #628, #635)

-

Adds Instruments and adapter protocol tests for the adapter rework (@bmoneke, #665)

-

Adds SR830 sync filter and reference source trigger controls (@AsafYagoda, #630)

-

Adds Keithley6221 phase marker phase and line support (@AsafYagoda, #629)

-

Adds missing docstrings for the Keithley 2306 battery simulator (@AidenDawn, #720)

-

Fix hcp instruments documentation (@bmoneke, #671)

-

Fix HPLegacyInstrument initializer API (@bilderbuchi, #684)

-

Fix Fwbell 5080 implementation (@mcdo0486, #714)

-

Fix broken documentation example. (@bmoneke, #738)

-

Corrects a typo in the Keithley 2600 driver (@mcdo0486, #615)

-

Removes ATS545 dynamic docstring use and makes the behavior more general (@AidenDawn, #685)

### Automation

-

Add storing unitful experiment results (@bmoneke, #642)

-

Adds condition storage in files (@CasperSchippers, #503)

### GUI

-

Add compatibility with Qt 6 (@CasperSchippers, #688)

-

Adds spinbox support for IntegerParameter and FloatParameter (@jarvas24, #656)

-

Adds the "delete data file" button to browser_item_menu (@jarvas24, #654)

-

Refactors windows.py into a folder of separate modules (@mcdo0486, #593)

-

Remove dependency on matplotlib (@msmttchr, #622)

-

Removes deprecated QtWidgets access through QtGui (@maederan201, #695)

### Miscellaneous

-

Refreshes and expands documentation (@bilderbuchi, #712, @bmoneke, #655)

-

Adds PEP517 compatibility and dynamic version-number lookup (@bilderbuchi, #613)

-

Adds an example and documentation for using a foreign instrument (@bmoneke, #647)

-

Add black configuration (@bleykauf, #683)

-

Removes VISAAdapter.has_supported_version() because it is no longer required.

### New Contributors

@jcarbelbide, @mroeleke, @bmoneke, @garzetti, @AsafYagoda, @AidenDawn, @LastStarDust, @sansanda

**Full Changelog**: [https://github.com/pymeasure/pymeasure/compare/v0.10.0…v0.11.0](https://github.com/pymeasure/pymeasure/compare/v0.10.0...v0.11.0)

### Version 0.10.0 (2022-04-09)

Primary highlights in this release:

-

23 new instrument drivers have been added

-

Adds dynamic Instrument properties whose parameters can change at runtime

-

Allows communication settings to be defined flexibly for each protocol

-

Adds Python 3.10 support and drops Python 3.6 support.

-

Merges many additions and improvements

### Instruments

-

Adds Agilent B1500 Data Formats and Documentation (@moritzj29)

-

New Anaheim Automation stepper motor controllers (@samcondon4)

-

New Andeen Hagerling capacitance bridges (@dkriegner)

-

Adds the Anritsu MS9740A Optical Spectrum Analyzer (@md12g12)

-

New BK Precision 9130B Instrument (@dennisfeng2)

-

New Edwards nXDS (10i) Vacuum Pump (@hududed)

-

New Fluke 7341 temperature bath instrument (@msmttchr)

-

New Heidenhain ND287 Position Display Unit Driver (@samcondon4)

-

New HP 3478A (@LongnoseRob)

-

Adds the HP 8116A 50 MHz Pulse/Function Generator (@CodingMarco)

-

New Keithley 2260B DC Power Supply (@bklebel)

-

New Keithley 2306 Dual Channel Battery/Charger Simulator (@mfikes)

-

New Keithley 2600 SourceMeter series (@Daivesd)

-

New Keysight N7776C Swept Laser Source (@maederan201)

-

New Lakeshore 421 (@CasperSchippers)

-

New Oxford IPS120-10 (@CasperSchippers)

-

New Pendulum CNT-91 frequency counter (@bleykauf)

-

New Rohde&Schwarz - SFM TV test transmitter (@LongnoseRob)

-

New Rohde&Schwarz FSL spectrum analyzer (@bleykauf)

-

New SR570 current amplifier driver (@pyMatJ)

-

New Stanford Research Systems SR510 instrument driver (@samcondon4)

-

New Toptica Smart Laser diode (@dkriegner)

-

New Yokogawa GS200 Instrument (@dennisfeng2)

-

Adds the output low grounded property to Keithley 6221 (@CasperSchippers)

-

Adds a shutdown function for Keithley 2260B (@bklebel)

-

Adds phase control for Agilent 33500 (@corna)

-

Allows assigning "ONCE" to auto_zero on Keithley 2400 (@mfikes)

-

Adds line frequency controls for Keithley 2400 (@mfikes)

-

Adds the LIA and ERR status byte read properties for the SRS Sr830 driver (@samcondon4)

-

Adds every command for Oxford Intelligent Temperature Controller 503 (@CasperSchippers)

-

Fix DSP 7265 lockin amplifier (@CasperSchippers)

-

Corrects a Keithley 6517B Electrometer bug (@CasperSchippers)

-

Fixes the deprecated visa.config call in Keithley2000 (@bklebel)

-

Corrects a bug in the Keithley 2700 (@CasperSchippers)

-

Fixes sensor flag setting for Thorlabs PM100D (@bleykauf)

-

Corrects the SCPI used for Keithley 2400 voltage NPLC (@mfikes)

-

Adds missing return statements in Tektronix AFG3152C (@bleykauf)

-

Fix DPSeriesMotorController bug (@samcondon4)

-

Fixes a Keithley2600 failure while retrieving an error code (@bicarlsen)

-

Updates Attocube ANC300 for the new SCPI Instrument properties (@dkriegner)

-

Fixes the wait_for_trigger bug in Agilent33220A (neal-kepler)

### GUI

-

Add time-estimator widget (@CasperSchippers)

-

Adds progress bar management (@msmttchr)

-

Remove broken errorbar feature (@CasperSchippers)

-

Changes the pyqtgraph pen width (@maederan201)

-

Make linewidth changeable (@CasperSchippers)

-

Generalizes the warning in the plotter section (@CasperSchippers)

-

Implements visibility groups in InputsWidgets (@CasperSchippers)

-

Adjusts ManagedWindow directory widget navigation (@jarvas24)

-

Improve Placeholder logic (@CasperSchippers)

-

Splits widgets into separate modules (@mcdo0486)

-

Fixes a PySide2 setSizePolicy bug (@msmttchr)

-

Fix managed window (@msmttchr)

-

Fix ListParameter for numbers (@moritzj29)

-

Corrects column display when showing data (@CasperSchippers)

-

Fix procedure property issue (@msmttchr)

-

Fix pyside2 (@msmttchr)

### Miscellaneous

-

Improve SCPI property support (@msmttchr)

-

Remove broken safeKeyword management (@msmttchr)

-

Add dynamic property support (@msmttchr)

-

Adds a flexible API for defining connection configuration (@bilderbuchi)

-

Adds write_binary_values() to SerialAdapter (@msmttchr)

-

Updates an outdated pyvisa ask() call to query() (@LongnoseRob)

-

Fix ZMQ bug (@bilderbuchi)

-

Documents tuple passing to control property (@bklebel)

-

Documentation bugfix (@CasperSchippers)

-

Repairs broken documentation links. (@samcondon4)

-

Updated widget documentation (@mcdo0486)

-

Fix typo SCIP->SCPI (@mfikes)

-

Remove Python 3.6, add Python 3.10 testing (@bilderbuchi)

-

Modernizes the code base with Python 3.7 features (@bilderbuchi)

-

Adds image data generation to the Mock Instrument class (@samcondon4)

-

Adds autodoc warnings to the problem matcher (@bilderbuchi)

-

Update CI & annotations (@bilderbuchi)

-

Test workers (@mcdo0486)

-

Change copyright date to 2022 (@LongnoseRob)

-

Removed unused code (@msmttchr)

### New Contributors

@LongnoseRob, @neal, @hududed, @corna, @Daivesd, @samcondon4, @maederan201, @bleykauf, @mfikes, @bicarlsen, @md12g12, @CodingMarco, @jarvas24, @mcdo0486!

**Full Changelog**: [https://github.com/pymeasure/pymeasure/compare/v0.9…v0.10.0](https://github.com/pymeasure/pymeasure/compare/v0.9...v0.10.0)

### Version 0.9 – released 2/7/21

-

PyMeasure officially moves to github.com/pymeasure/pymeasure

-

Adds Python 3.9 support and removes Python 3.5 because of EOL

-

Moves CI from TravisCI and Appveyor to GitHub Actions (@bilderbuchi)

-

Adds new functionality for Oxford Instruments ITC 503 (@CasperSchippers)

-

Adds Agilent 34450A and Keysight DSOX1102G instruments (@theMashUp, @jlarochelle)

-

Improvements to NI VirtualBench (@moritzj29)

-

New Agilent B1500 instrument (@moritzj29)

-

New Keithley 6517B instrument (@wehlgrundspitze)

-

Delivers major PyVISA compatibility improvements (@bilderbuchi, @msmttchr, @CasperSchippers, @cjermain)

-

New Anapico APSIN12G instrument (@StePhanino)

-

Improves Thorelabs Pro 8000 and SR830 (@Mike-HubGit)

-

New SR860 instrument (@StevenSiegl, @bklebel)

-

Fix to escape sequences (@tirkarthi)

-

Adds a directory input for ManagedWindow (@paulgoulain)

-

Adds TelnetAdapter and the Attocube ANC300 Piezo controller (@dkriegner)

-

New Agilent 34450A (@theMashUp)

-

New Razorbill RP100 strain cell controller (@pheowl)

-

Fixes ScientificInput and FloatParameter precision and default value handling (@moritzj29)

-

Fixes controls for Keithly 2400 and 2450 (@pyMatJ)

-

Improves Inputs and open_file_externally (@msmttchr)

-

Fixes to Agilent 8722ES (@alexmcnabb)

-

Fixes QThread cleanup (@neal-kepler, @msmttchr)

-

Fixes Keyboard interrupt handling and parameters (@CasperSchippers)

### Version 0.8 – released 3/29/19

-

Python 3.8 is now supported

-

Adds Measurement Sequencer for running across a large parameter space (@CasperSchippers)

-

Adds live image measurement plotting (@jmittelstaedt)

-

Improvements to VISA adapter (@moritzj29)

-

Added Tektronix AFG 3000, Keithley 2750 (@StePhanino, @dennisfeng2)

-

Documentation improvements (@mivade)

-

Fixes ScientificInput handling of float strings (@moritzj29)

-

New validator: strict_discrete_range (@moritzj29)

-

Improvements to Recorder thread joining

-

Moves the ReadtheDocs configuration to version 2

-

National Instruments Virtual Bench initial support (@moritzj29)

### Version 0.7 – released 8/4/19

-

Drops Python 3.4 support while adding Python 3.7 support

-

Significantly improves CI, dependencies, and the conda environment (@bilderbuchi, @cjermain)

-

Fixes the PyQT issue in ResultsDialog (@CasperSchippers)

-

Fixes the wire validator in Keithley 2400 (@Fattotora)

-

Adds source_enabled control for Keithley 2400 (@dennisfeng2)

-

Fixes the time constant and adds input controls for SR830 (@dennisfeng2)

-

Adds Keithley 2450 and Agilent 33521A (@hlgirard, @Endever42)

-

Adds proper escaping support for CSV headers (@feph)

-

Minor updates (@dvase)

### Version 0.6.1 – released 4/21/19

-

Adds Elektronica SM70-45D, Agilent 33220A, and Keysight N5767A instruments (@CasperSchippers, @sumatrae)

-

Fixes Prologix adapter and Keithley 2400 issues (@hlgirard, @ronan-sensome)

-

Improves SRS SR830 support (@CasperSchippers)

### Version 0.6 – released 1/14/19

-

Adds the VXI11 Adapter for ethernet instruments (@chweiser)

-

PyQt updates to 5.6.0

-

Adds instruments for SRS SG380, Ametek 7270, Agilent 4156, HP 34401A, Advantest R3767CG, plus Oxford ITC503 (@sylkar, @jmittelstaedt, @vik-s, @troylf, @CasperSchippers)

-

Updates instrument support for Keithley 2000, Agilent 8257D, ESP 300, and Keithley 2400 (@watersjason, @jmittelstaedt, @nup002)

-

Various minor bug fixes (@thosou)

### Version 0.5.1 – released 4/14/18

-

Handles PyVISA minor versions correctly

-

Documentation improvements (@Laogeodritt and @ederag)

-

Instruments now have `set_process` capability (@bilderbuchi)

-

Plotter now uses threads (@dvspirito)

-

Improves Display inputs and PlotItem (@Laogeodritt)

### Version 0.5 – released 10/18/17

-

Uses threads by default, avoiding multiprocessing spawn problems

-

Enhanced unit tests for threading

-

Adds Sphinx Doctests to the documentation (@bilderbuchi)

-

Improvements to documentation (@JuMaD)

### Version 0.4.6 – released 8/12/17

-

Reverts multiprocessing start method keyword arguments to resolve Unix spawn problems (@ndr37)

-

Fixes regressions in Results writing (@feinsteinben)

-

Fixes TCP support by using cloudpickle (@feinsteinben)

-

Restructing of unit test framework

### Version 0.4.5 – released 7/4/17

-

Updates Recorder and Scribe to use QueueListener (@feinsteinben)

-

Allows PrologixAdapter and SerialAdapter to handle Serial objects as adapters (@feinsteinben)

-

Uses cloudpickle for optional TCP support serialization (@feinsteinben)

-

Applies a large PEP8 review with bug fixes (@feinsteinben)

-

Packages docs in the code distribution (@ghisvail)

-

Adds continuous integration support for Python 3.6 (@feinsteinben)

### Version 0.4.4 – released 6/4/17

-

Fixes pip install for builds without wheels

-

Update to Agilent E4980 (@dvspirito)

-

Applies small docs, tests, and formatting fixes (@ghisvail, @feinsteinben)

### Version 0.4.3 – released 3/30/17

-

Adds instruments for Agilent E4980, AMI 430, Agilent 34410A, Thorlabs PM100, plus Anritsu MS9710C (@TvBMcMaster, @dvspirito, and @mhdg)

-

Updates to PyVISA support (@minhhaiphys)

-

Starts work on the resource manager (@dvspirito)

-

Fixes Prologix adapter behavior to allow read-write delays (@TvBMcMaster)

-

Fixes the conda environment used on continuous integration

### Version 0.4.2 – released 8/23/16

-

Adds new installation instructions for Anaconda and the conda-forge package (thanks @melund!)

-

Fixes bugs in Keithley 2000, SR830, and Agilent E4408B

-

Restores the Newport ESP300 motion controller

-

Updates Keithely 2400, 2000 and Yokogawa 7651 substantially to create a shared interface

-

Adds command-string processing hooks for Instrument property functions

-

Adds new features to the LakeShore 331 temperature controller

-

Updates the Agilent 8257D signal generator to expose more features

### Version 0.4.1 – released 7/31/16

-

Applies a critical setup.py fix for importing instruments, also documented

### Version 0.4 – released 7/29/16

-

Replaces Instrument add_measurement and add_control with measurement and control functions

-

Adds validators so Instrument.control can enforce restricted ranges

-

Adds mapping to Instrument.control for more flexible inputs

-

Uses Conda to configure the Python environment

-

macOS testing in continuous integration

-

Major updates to the documentation

### Version 0.3 – released 4/8/16

-

Adds IPython (Jupyter) notebook support with major features

-

Refreshes the example scripts and notebooks

-

New PyMeasure logo released

-

Removed support for Python <3.4

-

Changes multiprocessing to use spawn for compatibility

-

Significant work on the documentation

-

Adds the first tests for non-instrument code

-

Sets up continuous integration for Linux and Windows

### Version 0.2 – released 12/16/15

-

Adds Python 3 compatibility and removes Python 2 support

-

Renames many items for stronger PEP8 compliance

-

Added MIT License

-

Restructures the package substantially into smaller modules

-

Reworks display functionality substantially and introduces new Qt objects for easy extensions

-

Reworks procedure execution substantially, now using a Worker process that benefits from multi-core CPUs

-

Adds several examples

-

Adds Procedure listening methods and introduces ZMQ for TCP connectivity

-

Updates to Keithley2400 and VISAAdapter

### Version 0.1.6 – released 4/19/15

-

Renames Automate to PyMeasure so the package purpose is clearer

-

Adds VectorParameter so Procedures can accept vector input

-

Applies minor fixes for Results and Danfysik8500

### Version 0.1.5 – release 10/22/14

-

Adds a Manager class for queue-style Procedure handling

-

Adds a Browser that works with Manager to show the queue

-

Bug fixes for Results loading

### Version 0.1.4 – released 8/2/14

-

Integrates Results into display and file-writing behavior

-

Bug fixes for Listener classes

-

Bug fixes for SR830

### Version 0.1.3 – released 7/20/14

-

Replaces the logging system with the Python logging package

-

Adds data management through Results plus bug fixes for Procedures and Parameters

-

Adds pandas v0.14 to requirements for data management

-

Adds data listeners plus Qt4 and PyQtGraph helpers

### Version 0.1.2 – released 7/18/14

-

Bug fixes to LakeShore 425

-

Adds new Procedure and Parameter classes for generic experiments

-

Added version number in package

### Version 0.1.1 – released 7/16/14

-

Fixes bugs in PrologixAdapter, VISAAdapter, Agilent 8722ES, Agilent 8257D, Stanford SR830, and Danfysik8500

-

Adds Tektronix TDS 2000 with basic functionality

-

Fixes Danfysik communication so errors are handled properly

### Version 0.1.0 – released 7/15/14

-

Initial release
