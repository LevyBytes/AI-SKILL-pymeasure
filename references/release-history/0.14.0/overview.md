# Version 0.14.0 (2024-05-22)

Primary changes in this release:

- Add support for numpy 2.0

- Add support for python 3.12

- Academic citation support was improved with a current Zenodo DOI and citation metadata.

- A default `queue` method and `FileInputWidget` were added, making it faster to start using the PyMeasure interface (`ManagedWindow`).

- A `SCPIMixin` base class was added for instruments, replacing the pattern of defining `includeSCPI=True`.

- Instrument manufacturer modules are no longer imported from `pymeasure/instruments/__init__.py`. Previously, importing one instrument inside a procedure loaded every instrument into memory through the manufacturer modules referenced by `pymeasure/instruments/__init__.py`. Removing those imports lowers PyMeasure memory use when a single instrument is imported. Instrument classes now need imports from the manufacturer module or directly from the driver file. For example, change `from pymeasure.instruments import Extreme5000` to `from pymeasure.instruments.extreme import Extreme5000` or `from pymeasure.instruments.extreme.extreme5000 import Extreme5000`.

- 17 new instruments
