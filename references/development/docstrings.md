# Docstrings

Users can quickly extract important details from properties and methods when docstrings are descriptive and specific. Follow the [PEP257](https://peps.python.org/pep-0257/) docstring guidelines where possible, especially these points:

- Delimit docstrings with triple-quoted strings (`"""`).

- Write one brief summary line in the imperative mood and end it with a period.

- After a blank line, you may add extra detail.

- For functions and methods, parameter docs may be written with the [reStructuredText docstring format](https://www.sphinx-doc.org/en/master/usage/restructuredtext/domains.html#info-field-lists).

For properties, begin the docstring with "Control", "Get", "Measure", or "Set" because that property kind is otherwise not visible after import. This signals whether the property is gettable ("Get" or "Measure", for example with `measurement()`), settable ("Set", for a `setting()`), or both ("Control", for a `control()`). At the end of the summary line, it is also useful to include the type and any [Restricting values with validators](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#validators) information when applicable; examples appear throughout [Adding instruments](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html#adding-instruments). One valid docstring example is `"""Control the voltage in Volts (float strictly from -1 to 1)."""`.

Docstrings should contain information relevant to *using* a property/method. Do *not* include internal or hidden implementation details, such as the format of commands exchanged with the device.
