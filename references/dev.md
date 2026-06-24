# Coding Standards, Contribute

> Pymeasure reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Coding Standards; Contributing.

## Coding Standards

### Coding Standards

To keep PyMeasure instruments consistent across the repository, apply these standards.

### Python style guides

Follow the [PEP8 style guide](https://www.python.org/dev/peps/pep-0008/) together with the [PEP257 docstring conventions](https://www.python.org/dev/peps/pep-0257/).

Name functions and variables in lowercase, adding underscores where words need separation. Reserve CamelCase for class names, except in Qt-related code where CamelCase is normal.

A [ruff](https://docs.astral.sh/ruff/linter/) linter configuration is also included. The codebase should produce no warnings from it. Many editors/IDEs can run the linter as you edit and display inline findings. You can also run `ruff check` from the repository root to find issues. Automation on Github runs additional checkers too, but that feedback is much slower, so do not depend on it alone.

Using the [black](https://black.readthedocs.io/en/stable/) code formatter is permitted, not mandatory. When changing an existing file, prefer [darker](https://github.com/akaihola/darker) over black so unrelated formatting changes are not introduced. That keeps review attention on the implementation rather than formatting churn. `darker` is compatible with `black` and formats only regions Git reports as changed. If `black`/`darker` output disagrees with ruff, especially around [E203](https://www.flake8rules.com/rules/E203.html), treat ruff as authoritative. When appropriate, add `#noqa : E203` on a line to suppress E203 for that line.

Add type hints when useful. Every type hint should follow the guidance in the [typing](https://docs.python.org/3/library/typing.html) package.

### Documentation

PyMeasure uses reStructuredText and the [Sphinx documentation generator](http://www.sphinx-doc.org/en/stable/) for code documentation. Document all functions, classes, and methods with docstrings in the code; see section Docstrings.

### Usage of getter and setter functions

Avoid getter and setter functions because properties give a smoother user experience. PyMeasure has extensive property-definition tools, described in the sections beginning with [Writing properties](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#properties), so these property types are preferred.

### Docstrings

Users can quickly extract important details from properties and methods when docstrings are descriptive and specific. Follow the [PEP257](https://peps.python.org/pep-0257/) docstring guidelines where possible, especially these points:

-

Delimit docstrings with triple-quoted strings (`"""`).

-

Write one brief summary line in the imperative mood and end it with a period.

-

After a blank line, you may add extra detail.

-

For functions and methods, parameter docs may be written with the [reStructuredText docstring format](https://www.sphinx-doc.org/en/master/usage/restructuredtext/domains.html#info-field-lists).

For properties, begin the docstring with "Control", "Get", "Measure", or "Set" because that property kind is otherwise not visible after import. This signals whether the property is gettable ("Get" or "Measure", for example with `measurement()`), settable ("Set", for a `setting()`), or both ("Control", for a `control()`). At the end of the summary line, it is also useful to include the type and any [Restricting values with validators](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/properties.html#validators) information when applicable; examples appear throughout [Adding instruments](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html#adding-instruments). One valid docstring example is `"""Control the voltage in Volts (float strictly from -1 to 1)."""`.

Docstrings should contain information relevant to *using* a property/method. Do *not* include internal or hidden implementation details, such as the format of commands exchanged with the device.

## Contributing

### Contributing

Contributions to both the instrument repository and the main code base are strongly encouraged. This section gives new contributors the basic work-flow.

### Using the development version

PyMeasure development features land in the development version, which is hosted on [GitHub](https://github.com/). Source changes are tracked and managed with [Git version control](https://git-scm.com/). On Windows, [GitHub Desktop](https://git-scm.com/downloads) is recommended. Confirm that a suitable version of Git (or GitHub Desktop) is installed and that you have a GitHub account.

Confirm that `git --version` runs from the command line. If you use Github Desktop, each terminal window may need Git added to your path. In a windows anaconda prompt, use `set PATH="C:Users<USERNAME>AppDataLocalGitHubDesktopapp-<#######>resourcesappgitcmd";%PATH%`.

Before adding your feature, [fork](https://help.github.com/articles/fork-a-repo/) PyMeasure so the repository is copied under your GitHub account.

The steps below assume Anaconda has been set up as shown in the [Quick Start guide](https://pymeasure.readthedocs.io/en/latest/quick_start.html), and they give the required terminal commands. If you prefer GitHub Desktop, review [their documentation](https://help.github.com/desktop/) for the matching operations.

Clone the PyMeasure fork `your-github-username/pymeasure`. In the terminal examples that follow, substitute your chosen path and GitHub username.

```bash
cd /path/for/code
git clone https://github.com/your-github-username/pymeasure.git

```

If PyMeasure was previously installed with `pip`, uninstall that copy before proceeding.

```bash
pip uninstall pymeasure

```

Install PyMeasure in editable mode with the optional extras selected.

```bash
cd /path/for/code/pymeasure
pip install -e .[gui,tests,docs]

```

The `-e` option lets you edit PyMeasure files and have those changes show up. The bracketed extra groups enable tests and local documentation builds. After doing this, reset your notebook kernel or Python console. You now have your own installed copy of the PyMeasure development version.

Depending on your Python installation, you may see an error saying that the file setup.py is missing or something similar. Updating pip may fix it.

```bash
python -m pip install pip --upgrade

```

### Working on a new feature

Git branches let several features be developed at the same time without conflicts. The master branch holds the stable development version. Create your branch from master rather than working directly on master, then merge it back into master when the work is done.

Before changing code, create a feature branch. For example, adding the instrument "Extreme 5000" would use a branch named "dev/extreme-5000".

```bash
git branch dev/extreme-5000

```

A branch can also be created on GitHub with [make a new branch](https://help.github.com/articles/creating-and-deleting-branches-within-your-repository/). In that case, fetch the changes before the branch appears on your local computer.

```bash
git fetch

```

After creating the branch, switch the current branch to the new branch.

```bash
git checkout dev/extreme-5000

```

At this point you can implement the feature and edit the code. For consistency, follow the [coding standards for PyMeasure](https://pymeasure.readthedocs.io/en/latest/dev/coding_standards.html). Use `git status` to inspect changed files. Commit your work as you proceed and push it to your fork.

```bash
git add file-that-changed.py
git commit -m "A short description about what changed"
git push

```

### Making a pull request

As work progresses, it is useful to open a pull request (PR) against the `master` branch of `pymeasure/pymeasure`. This gives other contributors a place to discuss the feature with you. Opening the pull request after the first commit is encouraged. If it is still early, mark the pull request as a draft.

On the [PyMeasure GitHub page](https://github.com/pymeasure/pymeasure), [start a pull request](https://help.github.com/articles/using-pull-requests/).

Automation runs the unit tests and checks selected coding standards. Problems to fix, such as linting or docstring warnings, appear as annotations in the "Files changed" tab.

PyMeasure maintainers will review your pull-request. Feedback often leads to discussion and iteration before the pull request can be merged, either in the conversation tab or inline code comments.

Because maintainer manpower is limited, PR review and/or merge may take a long time. Review effort generally grows poorly as PR size increases. For that reason, **smaller PRs are much preferred**; Contribution standards has more detail.

When your contribution is on its own branch as recommended above, you can use it meanwhile by checking out that feature branch instead of master.

### Contribution standards

Every contribution, whether human or AI-assisted, must:

1.

Follow the [coding standards](https://pymeasure.readthedocs.io/en/latest/dev/coding_standards.html).

2.

Be checked *by the contributor* before it is submitted.

3.

Keep the focus on **single logical changes** and avoid "shotgun" PRs. Try to restrict the contribution to one "aspect", such as one instrument, a small set of closely related instruments, one bug fix, or one feature.

4.

Use clear documentation and atomic commits to respect reviewer time.

**For AI-assisted contributions:**

-

Use AI as a pair programmer; *you* remain accountable for what it produces.

-

Code must meet the same review bar as human-written contributions.

-

A PR may be rejected under these guidelines if it appears to contain unreviewed generated output, such as hallucinated APIs, style inconsistencies, or boilerplate that does not match the codebase.

Hint

Remember that the commit carries your name. Whether the code came from your keyboard, Copilot, or ChatGPT, *you* are responsible for its quality.

### Unit testing

Unit tests run whenever a new commit is made on a branch. Their role is to catch changes that break existing functionality by testing each feature unit. PyMeasure relies on [pytest](http://pytest.org/latest/) for this testing. They run on TravisCI and Appveyor for Linux/macOS and Windows respectively.

Developing with the unit tests running is strongly encouraged. Doing so helps ensure your contribution works when you open a pull request.

```bash
pytest

```

When your feature is testable, unit tests are required. This keeps the feature working as new features are introduced.

You now know the pieces of the PyMeasure development work-flow. We look forward to your pull-request!
