# Instruments (part 1)

> Pymeasure reference. Original prose; identifiers preserved verbatim.

### pymeasure.instruments

Documentation for PyMeasure instrument classes is collected in this section.

- [Instrument classes](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html)
  - [`CommonBase`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase)
  - [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)
  - [`Channel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel)
  - [`FakeInstrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.fakes.FakeInstrument)
  - [`SwissArmyFake`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.fakes.SwissArmyFake)

- [Generic Instrument Types Mixins](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html)
  - [`SCPIMixin`](https://pymeasure.readthedocs.io/en/latest/api/instruments/generic_types.html#pymeasure.instruments.generic_types.SCPIMixin)

- [Validator functions](https://pymeasure.readthedocs.io/en/latest/api/instruments/validators.html)
- [Comedi data acquisition](https://pymeasure.readthedocs.io/en/latest/api/instruments/comedi.html)
  - [`getAI()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/comedi.html#pymeasure.instruments.comedi.getAI)
  - [`getAO()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/comedi.html#pymeasure.instruments.comedi.getAO)
  - [`readAI()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/comedi.html#pymeasure.instruments.comedi.readAI)
  - [`writeAO()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/comedi.html#pymeasure.instruments.comedi.writeAO)

- [Resource Manager](https://pymeasure.readthedocs.io/en/latest/api/instruments/resources.html)
  - [`list_resources()`](https://pymeasure.readthedocs.io/en/latest/api/instruments/resources.html#pymeasure.instruments.list_resources)

Instruments by manufacturer:

- [Active Technologies](https://pymeasure.readthedocs.io/en/latest/api/instruments/activetechnologies/index.html)
  - [Active Technologies AWG-401x 1.2GS/s Arbitrary Waveform Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/activetechnologies/AWG401x.html)

- [Aculight](https://pymeasure.readthedocs.io/en/latest/api/instruments/aculight/index.html)
  - [Aculight Argos 2400 OPO system](https://pymeasure.readthedocs.io/en/latest/api/instruments/aculight/argos.html)

- [Advantest](https://pymeasure.readthedocs.io/en/latest/api/instruments/advantest/index.html)
  - [Advantest R3767CG Vector Network Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/advantest/advantestR3767CG.html)
  - [Advantest R6245/R6246 DC Voltage/Current Sources/Monitors](https://pymeasure.readthedocs.io/en/latest/api/instruments/advantest/advantestR624X.html)

- [Agilent](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/index.html)
  - [Agilent 8257D Signal Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent8257D.html)
  - [Agilent 8722ES Vector Network Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent8722ES.html)
  - [Agilent E4408B Spectrum Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE4408B.html)
  - [Agilent E4980 LCR Meter](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE4980.html)
  - [Agilent E5062A VNA](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE5062A.html)
  - [Agilent 34410A digital multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent34410A.html)
  - [HP/Agilent/Keysight 34450A digital multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent34450A.html)
  - [Agilent 4155/4156 Semiconductor Parameter Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4156.html)
  - [Agilent 4294A precision impedance analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4294A.html)
  - [Agilent 33220A arbitrary waveform generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33220A.html)
  - [Agilent 33500 Function/Arbitrary Waveform Generator Family](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33500.html)
  - [Agilent 33521A function and arbitrary waveform generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent33521A.html)
  - [Agilent B1500 Semiconductor Parameter Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentB1500.html)
  - [Agilent 4284A LCR meter](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilent4284A.html)
  - [Agilent B2980 Series, Femto/Picoammeter Electrometer/High Resistance Meter](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentB298x.html)
  - [Agilent E5270B SMU mainframe](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentE5270B.html)
  - [Agilent N8975A noise figure analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/agilentN8975A.html)

- [Aim-TTI](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/index.html)
  - [Aim-TTI PL Series Power Supplies](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/aimttiPL.html)
  - [Aim-TTi Electronic Loads](https://pymeasure.readthedocs.io/en/latest/api/instruments/aimtti/ld400p.html)

- [AJA International](https://pymeasure.readthedocs.io/en/latest/api/instruments/aja/index.html)
  - [AJA DCXS-750 or 1500 power supply for DC magnetron sputtering](https://pymeasure.readthedocs.io/en/latest/api/instruments/aja/DCXS.html)

- [Ametek](https://pymeasure.readthedocs.io/en/latest/api/instruments/ametek/index.html)
  - [Ametek 7270 DSP Lockin Amplifier](https://pymeasure.readthedocs.io/en/latest/api/instruments/ametek/ametek7270.html)

- [AMI](https://pymeasure.readthedocs.io/en/latest/api/instruments/ami/index.html)
  - [AMI 430 Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/ami/ami430.html)

- [Anaheim Automation](https://pymeasure.readthedocs.io/en/latest/api/instruments/anaheimautomation/index.html)
  - [DP-Series Step Motor Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/anaheimautomation/dpseriesstepmotorcontroller.html)

- [Anapico](https://pymeasure.readthedocs.io/en/latest/api/instruments/anapico/index.html)
  - [Anapico APSIN12G Signal Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/anapico/apsin12G.html)

- [Andeen Hagerling](https://pymeasure.readthedocs.io/en/latest/api/instruments/andeenhagerling/index.html)
  - [Andeen Hagerling AH2500A capacitance bridge](https://pymeasure.readthedocs.io/en/latest/api/instruments/andeenhagerling/ah2500a.html)
  - [Andeen Hagerling AH2700A capacitance bridge](https://pymeasure.readthedocs.io/en/latest/api/instruments/andeenhagerling/ah2700a.html)

- [Anritsu](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/index.html)
  - [Anritsu MG3692C Signal Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMG3692C.html)
  - [Anritsu MS9710C Optical Spectrum Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS9710C.html)
  - [Anritsu MS9740A optical spectrum analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS9740A.html)
  - [Anritsu MS2090A handheld spectrum analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS2090A.html)
  - [Anritsu MS464xB Vector Network Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/anritsu/anritsuMS464xB.html)

- [Attocube](https://pymeasure.readthedocs.io/en/latest/api/instruments/attocube/index.html)
  - [Attocube ANC300 Motion Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/attocube/anc300.html)

- [BK Precision](https://pymeasure.readthedocs.io/en/latest/api/instruments/bkprecision/index.html)
  - [BK Precision 9130B DC Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/bkprecision/bkprecision9130b.html)

- [Danfysik](https://pymeasure.readthedocs.io/en/latest/api/instruments/danfysik/index.html)
  - [Danfysik 8500 Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/danfysik/danfysik8500.html)

- [Delta Elektronika](https://pymeasure.readthedocs.io/en/latest/api/instruments/deltaelektronica/index.html)
  - [Delta Elektronica SM7045D Power source](https://pymeasure.readthedocs.io/en/latest/api/instruments/deltaelektronica/sm7045d.html)

- [Edwards](https://pymeasure.readthedocs.io/en/latest/api/instruments/edwards/index.html)
  - [Edwards nxds vacuum pump](https://pymeasure.readthedocs.io/en/latest/api/instruments/edwards/nxds.html)

- [EURO TEST](https://pymeasure.readthedocs.io/en/latest/api/instruments/eurotest/index.html)
  - [Euro Test HPP120256 High Voltage Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/eurotest/eurotestHPP120256.html)

- [Fluke](https://pymeasure.readthedocs.io/en/latest/api/instruments/fluke/index.html)
  - [Fluke 7341 Temperature bath](https://pymeasure.readthedocs.io/en/latest/api/instruments/fluke/fluke7341.html)

- [FormFactor](https://pymeasure.readthedocs.io/en/latest/api/instruments/formfactor/index.html)
  - [FormFactor Velox Wafer Prober](https://pymeasure.readthedocs.io/en/latest/api/instruments/formfactor/velox.html)

- [F.W. Bell](https://pymeasure.readthedocs.io/en/latest/api/instruments/fwbell/index.html)
  - [F.W. Bell 5080 Handheld Gaussmeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/fwbell/fwbell5080.html)

- [Heidenhain](https://pymeasure.readthedocs.io/en/latest/api/instruments/heidenhain/index.html)
  - [Heidenhain ND287 Position Display Unit](https://pymeasure.readthedocs.io/en/latest/api/instruments/heidenhain/nd287.html)

- [HC Photonics](https://pymeasure.readthedocs.io/en/latest/api/instruments/hcp/index.html)
  - [HCP TC038 crystal oven](https://pymeasure.readthedocs.io/en/latest/api/instruments/hcp/tc038.html)
  - [HCP TC038D crystal oven](https://pymeasure.readthedocs.io/en/latest/api/instruments/hcp/tc038d.html)

- [Hewlett Packard](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/index.html)
  - [HP 33120A arbitrary waveform generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp33120A.html)
  - [HP 34401A multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp34401A.html)
  - [HP 3437A system voltmeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp3437A.html)
  - [HP 3478A multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp3478A.html)
  - [HP 8116A 50 MHz pulse and function generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8116A.html)
  - [HP 8560A / 8561B spectrum analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp856xx.html)
  - [HP Signal generator HP8657B](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8657B.html)
  - [HP 8753E Vector Network Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8753E.html)
  - [HP 11713A attenuator and switch driver](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html)
  - [HP 437B Power Meter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp437B.html)
  - [Support class for legacy HP devices](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hplegacyinstrument.html)
  - [HP System Power Supplies HP663XA](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hpsystempsu.html)

- [ILX Lightwave](https://pymeasure.readthedocs.io/en/latest/api/instruments/ilxlightwave/index.html)
  - [ILX Lighwave LDP3811](https://pymeasure.readthedocs.io/en/latest/api/instruments/ilxlightwave/ldp3811.html)

- [Inficon](https://pymeasure.readthedocs.io/en/latest/api/instruments/inficon/index.html)
  - [Inficon SQM-160 multi-film rate/thickness monitor](https://pymeasure.readthedocs.io/en/latest/api/instruments/inficon/sqm160.html)

- [IPG Photonics](https://pymeasure.readthedocs.io/en/latest/api/instruments/ipgphotonics/index.html)
  - [YAR fiber amplifier series](https://pymeasure.readthedocs.io/en/latest/api/instruments/ipgphotonics/yar.html)

- [Keithley](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/index.html)
  - [Keithley 2000 Multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2000.html)
  - [Keithley 2200 Series Power Supplies](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2200.html)
  - [Keithley 2260B DC Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2260B.html)
  - [Keithley 2281S power supply with battery simulator and characterizer features](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2281S.html)
  - [Keithley 2306 Dual Channel Battery/Charger Simulator](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2306.html)
  - [Keithley 2400 SourceMeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2400.html)
  - [Keithley 2400 SourceMeter (Legacy)](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2400_legacy.html)
  - [Keithley 2450 SourceMeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2450.html)
  - [Keithley 2510 TEC SourceMeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2510.html)
  - [Keithley 2600 SourceMeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2600.html)
  - [Keithley 2700 MultiMeter/Switch System](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2700.html)
  - [Keithley 2750 Multimeter/Switch System](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2750.html)
  - [Keithley 6221 current source for AC and DC operation](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley6221.html)
  - [Keithley 6517B Electrometer](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley6517b.html)
  - [Keithley DMM6500 Multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithleyDMM6500.html)
  - [Keithley 2182 Nanovoltmeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley2182.html)
  - [Keithley DAQ6510 Data Acquisition Logging Multimeter System](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithleyDAQ6510.html)
  - [Keithley 4200A-SCS parameter analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/keithley/keithley4200.html)

- [KEPCO INC.](https://pymeasure.readthedocs.io/en/latest/api/instruments/kepco/index.html)
  - [BOP bipolar power supply using a BIT 4886 digital interface card](https://pymeasure.readthedocs.io/en/latest/api/instruments/kepco/KepcoBOP.html)

- [Keysight](https://pymeasure.readthedocs.io/en/latest/api/instruments/keysight/index.html)
  - [Keysight DSOX1102G Oscilloscope](https://pymeasure.readthedocs.io/en/latest/api/instruments/keysight/keysightDSOX1102G.html)
  - [Keysight N5767A power supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/keysight/keysightN5767A.html)
  - [Keysight N5776C Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/keysight/keysightN7776C.html)
  - [Keysight E36312A triple-output power supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/keysight/keysightE36312A.html)
  - [Keysight E3631A triple-output power supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/keysight/keysightE3631A.html)
  - [Keysight 81160A pulse, function, arbitrary, and noise generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/keysight/keysight81160A.html)
  - [Keysight 33250A function and arbitrary waveform generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/keysight/keysight33250A.html)
  - [Keysight PNA Vector Network Analyzers](https://pymeasure.readthedocs.io/en/latest/api/instruments/keysight/keysightPNA.html)

- [Kuhne Electronic](https://pymeasure.readthedocs.io/en/latest/api/instruments/kuhneelectronic/index.html)
  - [KU SG 2.45 250 A microwave generator for the 2.45 GHz ISM-Band](https://pymeasure.readthedocs.io/en/latest/api/instruments/kuhneelectronic/kusg245_250a.html)

- [Lake Shore Cryogenics](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html)
  - [Lake Shore 211 Temperature Monitor](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore211.html)
  - [Lake Shore 224 Temperature Monitor](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore224.html)
  - [Lake Shore 331 Temperature Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore331.html)
  - [Lake Shore 3xx Temperature Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore3xx.html)
  - [Lake Shore 421 Gaussmeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore421.html)
  - [Lake Shore 425 Gaussmeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/lakeshore425.html)
  - [LakeShore Channel Classes](https://pymeasure.readthedocs.io/en/latest/api/instruments/lakeshore/index.html#lakeshore-channel-classes)

- [LeCroy](https://pymeasure.readthedocs.io/en/latest/api/instruments/lecroy/index.html)
  - [LeCroy T3DSO1204 Oscilloscope](https://pymeasure.readthedocs.io/en/latest/api/instruments/lecroy/lecroyT3DSO1204.html)

- [MKS Instruments](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/index.html)
  - [MKS Instruments Abstract Instrument](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mksinst.html)
  - [MKS Instruments 937B Vacuum Gauge Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mks937b.html)
  - [MKS Instruments 974B Vacuum Pressure Transducer](https://pymeasure.readthedocs.io/en/latest/api/instruments/mksinst/mks974b.html)

- [Newport](https://pymeasure.readthedocs.io/en/latest/api/instruments/newport/index.html)
  - [ESP 300 Motion Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/newport/esp300.html)

- [National Instruments](https://pymeasure.readthedocs.io/en/latest/api/instruments/ni/index.html)
  - [NI Virtual Bench](https://pymeasure.readthedocs.io/en/latest/api/instruments/ni/virtualbench.html)

- [Novanta Photonics](https://pymeasure.readthedocs.io/en/latest/api/instruments/novanta/index.html)
  - [Novanta FPU60 laser power supply unit](https://pymeasure.readthedocs.io/en/latest/api/instruments/novanta/fpu60.html)

- [Ophir](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/index.html)
  - [Ophir Base](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/ophir_base.html)
  - [Nova](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/nova.html)
  - [Nova II](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/novaII.html)
  - [Vega](https://pymeasure.readthedocs.io/en/latest/api/instruments/ophir/vega.html)

- [Oxford Instruments](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/index.html)
  - [Oxford Instruments Base Instrument](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/base.html)
  - [Oxford Instruments Intelligent Temperature Controller 503](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/ITC503.html)
  - [Oxford Instruments Intelligent Power Supply 120-10 used with superconducting magnets](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/IPS120_10.html)
  - [Oxford Instruments Mercury Intelligent Temperature Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/MercuryiTC.html)
  - [Oxford Instruments Power Supply 120-10 used with superconducting magnets](https://pymeasure.readthedocs.io/en/latest/api/instruments/oxfordinstruments/PS120_10.html)

- [Parker](https://pymeasure.readthedocs.io/en/latest/api/instruments/parker/index.html)
  - [Parker GV6 Servo Motor Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/parker/parkerGV6.html)

- [Philips](https://pymeasure.readthedocs.io/en/latest/api/instruments/philips/index.html)
  - [Philips PM 6669 Universal Frequency Counter](https://pymeasure.readthedocs.io/en/latest/api/instruments/philips/PM6669.html)

- [Pendulum](https://pymeasure.readthedocs.io/en/latest/api/instruments/pendulum/index.html)
  - [Pendulum CNT91 frequency counter](https://pymeasure.readthedocs.io/en/latest/api/instruments/pendulum/cnt91.html)

- [Proterial](https://pymeasure.readthedocs.io/en/latest/api/instruments/proterial/index.html)
  - [ROD-4 MFC Controller](https://pymeasure.readthedocs.io/en/latest/api/instruments/proterial/rod4.html)

- [PTW Freiburg](https://pymeasure.readthedocs.io/en/latest/api/instruments/ptw/index.html)
  - [PTW DIAMENTOR DAP dosemeters](https://pymeasure.readthedocs.io/en/latest/api/instruments/ptw/ptwDIAMENTOR.html)
  - [PTW UNIDOS Tango/Romeo dosemeters](https://pymeasure.readthedocs.io/en/latest/api/instruments/ptw/ptwUNIDOS.html)

- [Racal-Dana](https://pymeasure.readthedocs.io/en/latest/api/instruments/racal/index.html)
  - [Racal-Dana 1992 Universal Counter](https://pymeasure.readthedocs.io/en/latest/api/instruments/racal/racal1992.html)

- [Razorbill](https://pymeasure.readthedocs.io/en/latest/api/instruments/razorbill/index.html)
  - [Razorbill RP100 custrom power supply for Razorbill Instrums stress and strain cells](https://pymeasure.readthedocs.io/en/latest/api/instruments/razorbill/razorbillRP100.html)

- [Redpitaya](https://pymeasure.readthedocs.io/en/latest/api/instruments/redpitaya/index.html)
  - [Redpitaya board for analog acquisition, analog generation, and digital input/output](https://pymeasure.readthedocs.io/en/latest/api/instruments/redpitaya/redpitaya_scpi.html)

- [Rigol](https://pymeasure.readthedocs.io/en/latest/api/instruments/rigol/index.html)
  - [Rigol DG800 waveform generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/rigol/rigol_dg800.html)

- [Rohde & Schwarz](https://pymeasure.readthedocs.io/en/latest/api/instruments/rohdeschwarz/index.html)
  - [R&S SFM TV test transmitter](https://pymeasure.readthedocs.io/en/latest/api/instruments/rohdeschwarz/sfm.html)
  - [R&S FS Series spectrum analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/rohdeschwarz/fsseries.html)
  - [R&S HMP4040 Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/rohdeschwarz/hmp.html)

- [Santec](https://pymeasure.readthedocs.io/en/latest/api/instruments/santec/index.html)
  - [Santec TSL-500 Series Tunable Laser](https://pymeasure.readthedocs.io/en/latest/api/instruments/santec/tsl500series.html)
  - [Santec TSL-570 Tunable Laser](https://pymeasure.readthedocs.io/en/latest/api/instruments/santec/tsl570.html)
  - [Santec TSL-550 Tunable Laser](https://pymeasure.readthedocs.io/en/latest/api/instruments/santec/tsl550.html)

- [Siglent Technologies](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/index.html)
  - [Siglent Technologies Base Class](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spdbase.html)
  - [Siglent SPD1168X Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spd1168x.html)
  - [Siglent SPD1305X Power Supply](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_spd1305x.html)
  - [Siglent SDS1072CML Oscilloscope](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_sds1072cml.html)
  - [Siglent SDS1000XHD Oscilloscope](https://pymeasure.readthedocs.io/en/latest/api/instruments/siglenttechnologies/siglent_sds1000xhd.html)

- [Signal Recovery](https://pymeasure.readthedocs.io/en/latest/api/instruments/signalrecovery/index.html)
  - [DSP 7225 lock-in amplifier](https://pymeasure.readthedocs.io/en/latest/api/instruments/signalrecovery/dsp7225.html)
  - [DSP 7265 lock-in amplifier](https://pymeasure.readthedocs.io/en/latest/api/instruments/signalrecovery/dsp7265.html)
