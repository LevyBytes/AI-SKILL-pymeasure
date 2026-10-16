# instruments documentation links

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

Several Lakeshore instruments are built around channels and rely on the [Channel Interface](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/channels.html#channels). Temperature monitoring and controller instruments use these common [`Channel Classes`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Channel):
