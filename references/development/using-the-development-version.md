# Using the development version

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
