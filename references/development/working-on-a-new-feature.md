# Working on a new feature

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
