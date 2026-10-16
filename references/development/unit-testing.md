# Unit testing

Unit tests run whenever a new commit is made on a branch. Their role is to catch changes that break existing functionality by testing each feature unit. PyMeasure relies on [pytest](http://pytest.org/latest/) for this testing. They run on TravisCI and Appveyor for Linux/macOS and Windows respectively.

Developing with the unit tests running is strongly encouraged. Doing so helps ensure your contribution works when you open a pull request.

```bash
pytest

```

When your feature is testable, unit tests are required. This keeps the feature working as new features are introduced.

You now know the pieces of the PyMeasure development work-flow. We look forward to your pull-request!
