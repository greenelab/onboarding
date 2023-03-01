# Install Linter to Automatically Run Before Git Commit

## About

This section describes how to set up running a liner uploading code onto a GitHub repository (git commit ... -> git push).
A [linter](https://en.wikipedia.org/wiki/Lint_(software)) is a code analysis tool designed to analyze code and flag for programming errors, bugs and stylistic errors.
This tool allows one to drastically improve their productivity when writing code for their research projects as stylistic errors and programming errors will automatically be covered through this set-up.
Disclaimer: The following instructions only work for python code as R doesn't have a working linter. (Subject to change if new information were to come out on this fact.)

## Programs and Packages needed to set up Pipeline

Make sure [conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/download.html) or another python package manager is installed on your computer.
This pipeline is designed to run on python >=3.5.

This setup will also use the following packages (versions can be changed as needed):
1. pre-commit==2.9.3
2. black==20.8b1 
3. jupytext==1.9.1
4. flake8==3.8.4

## Installation Instructions

1. Set up your python environment to use python>=3.5 
2. Call ``pip install pre-commit==2.9.3``
3. call ``pip install black==22.3.0``
4. Create a file with the extension .pre-commit-config.yaml and fill in with lines of code reproduced in the [Configuration Files](#Pre-commit) section
5. Create a file with the extension .flake8 and fill in with lines of code reproduced in the [Configuration Files](#Flake8) section
6. Create a file with the extension .toml and fill in with lines of code reproduced in the [Configuration Files](#Black) section
7. Then call command ``pre-commit install`` to install the pipeline to run after the ``git commit`` command is called.
8. Now the pipeline is installed, and you can test it by calling ``pre-commit``.
9. Now you can proceed with normal code development and GitHub processes
10. When you call `git commit`, you will see a few checks being at the start of the committing process.
11. Checkpoints will fail as files are modified or flake8 errors persist
12. Review that changes files are to one's liking or manually make changes
13. Lastly, call ``git add`` on the changed files then call the same ``git commit`` command again.

## Warnings

This pipeline is designed to run black on jupyter notebooks and does not run on individual python scripts.
The flake8 step will complain about non-formatted python scripts as no changes would have been made at that point.
Simply run the command `black <python script>` and re-add the changed file.

## Configuration Files 

### Pre-commit

```yaml
repos:

- repo: https://github.com/mwouts/jupytext
  rev: 41b7e9c93b50da1d6feb486aceb2c4d534374090
  hooks:
  - id: jupytext
    name: jupytext_auto_linter
    args: [--set-formats, 'ipynb,py', --from, ipynb, --pipe, black, --to, py:light, --sync]

- repo: https://gitlab.com/pycqa/flake8
  rev: 6de8252c035844f1e679f509b5f37340b44d5c39
  hooks:
  - id: flake8

-   repo: https://github.com/pre-commit/pre-commit-hooks
    rev: 43f5ffaeab549e15168317892bf217dd450aa41b
    hooks:
    - id: trailing-whitespace
```

#### Pre-commit with Specified Folders

If one wants to allocate all scripts to one folder and notebooks to another folder use this file instead.
Just replace notebooks and scripts with the filenames you need. [Documentation here](https://github.com/mwouts/jupytext/blob/master/docs/config.md#per-notebook-configuration)

```yaml
repos:

- repo: https://github.com/mwouts/jupytext
  rev: 41b7e9c93b50da1d6feb486aceb2c4d534374090
  hooks:
  - id: jupytext
    name: jupytext_auto_linter
    args: [--set-formats, 'notebook_folder_path//ipynb, script_folder_path//py', --from, ipynb, --pipe, black, --to, py:light, --sync]

- repo: https://gitlab.com/pycqa/flake8
  rev: 6de8252c035844f1e679f509b5f37340b44d5c39
  hooks:
  - id: flake8

-   repo: https://github.com/pre-commit/pre-commit-hooks
    rev: 43f5ffaeab549e15168317892bf217dd450aa41b
    hooks:
    - id: trailing-whitespace
```

Depending on repository organization some may want to have files be in specific folders rather than in a centralized way.
Currently, there isn't a great way to accomplish this feature without manually calling ``jupytext --set-formats 'notebook_folder_path//ipynb,script_folder_path//py' notebook_folder_path/<notebook name>.ipynb``.
Then, remove the ``--set-formats, 'notebook_folder_path//ipynb, script_folder_path//py'`` part from the config file and run pre-commit like normal.

### Flake8

```yaml
[flake8]
ignore = E266, E501, W503, F403, F401, W391, E203
max-line-length = 79
max-complexity = 18
select = B,C,E,F,W,T4,B9
```

### Black

```yaml
[tool.black]
line-length = 79
include = '\.pyi?$'
exclude = '''
/(
    \.git
  | \.hg
  | \.mypy_cache
  | \.tox
  | \.venv
  | _build
  | buck-out
  | build
  | dist
)/
'''
```
