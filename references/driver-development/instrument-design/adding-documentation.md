# Adding documentation

Each instrument must have documentation, both as a requirement and to explain the implemented features to other users. Create a new reStructuredText file in the documentation.

```none
pymeasure/docs/api/instruments/extreme/
    |--> index.rst
    |--> extreme5000.rst

```

Start from an existing instrument documentation file; that copied pattern will auto-generate the instrument docs. In `index.rst`, link to the `extreme5000` file. When the manufacturer is new, also add that manufacturer in `pymeasure/docs/api/instruments/index.rst`.
