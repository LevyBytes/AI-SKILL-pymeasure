# Python style guides

Follow the [PEP8 style guide](https://www.python.org/dev/peps/pep-0008/) together with the [PEP257 docstring conventions](https://www.python.org/dev/peps/pep-0257/).

Name functions and variables in lowercase, adding underscores where words need separation. Reserve CamelCase for class names, except in Qt-related code where CamelCase is normal.

A [ruff](https://docs.astral.sh/ruff/linter/) linter configuration is also included. The codebase should produce no warnings from it. Many editors/IDEs can run the linter as you edit and display inline findings. You can also run `ruff check` from the repository root to find issues. Automation on Github runs additional checkers too, but that feedback is much slower, so do not depend on it alone.

Using the [black](https://black.readthedocs.io/en/stable/) code formatter is permitted, not mandatory. When changing an existing file, prefer [darker](https://github.com/akaihola/darker) over black so unrelated formatting changes are not introduced. That keeps review attention on the implementation rather than formatting churn. `darker` is compatible with `black` and formats only regions Git reports as changed. If `black`/`darker` output disagrees with ruff, especially around [E203](https://www.flake8rules.com/rules/E203.html), treat ruff as authoritative. When appropriate, add `#noqa : E203` on a line to suppress E203 for that line.

Add type hints when useful. Every type hint should follow the guidance in the [typing](https://docs.python.org/3/library/typing.html) package.
