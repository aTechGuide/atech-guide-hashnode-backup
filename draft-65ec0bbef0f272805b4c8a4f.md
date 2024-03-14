---
title: "Step-by-Step Guide: Installing Python "The Right Way" on a MacBook for Beginners (2024 Edition)"
slug: install-python-on-mac-beginner-step-by-step-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1710206419633/bdd5e5aa-de34-4ec9-8dfe-3f69333ecb46.jpeg

---

## Can You Relate?

👉 You want a step-by-step foolproof guide to install Python on a MacBook

👉 You have faced ***Version Conflicts***, i.e., different projects may require different Python versions, leading to conflicts and difficulties in managing the appropriate version for each project.

👉 You have faced ***Environment Pollution***, i.e., installing various packages globally can pollute the global namespace, leading to issues where one project's dependencies interfere with another's.

👉 You have faced ***Difficulty in Replication***, i.e., setting up an identical development environment on a different machine becomes cumbersome, as it requires manually ensuring the same versions of Python and all dependencies are installed.

👉 You have faced ***Risk of Breaking the System***, where installing and uninstalling packages globally can potentially lead to system-wide issues, especially if critical system dependencies are accidentally removed or overwritten.

If the answer is “yes” to any of the above,

Read this page carefully.

## TLDR

This guide provides a detailed, step-by-step process for installing Python on a MacBook, specifically for beginners.

It introduces Homebrew for initial setup, then focuses on using PyEnv to manage multiple Python versions and PyEnv Virtualenv for creating isolated project environments.

This approach helps avoid common issues like version conflicts, environment pollution, ensuring a smoother Python setup and project management experience on macOS.

## Pre Requisites

* MacBook
    
* Homebrew Installation
    

> Homebrew for Mac is a free and open-source software package management system that simplifies the installation of software on macOS and Linux.

### Homebrew Installation

Run `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"` to install Homebrew

A naive way of installing python on MacBook is via downloading

Let's begin installing Python on a Mac via.

## 1 PyEnv

* This tool helps in installing and easily switching between multiple versions of Python.
    
* We can set *Global Python* version on a per-user basis.
    
* We can set *Per Project* Python versions.
    

### 1a Installing PyEnv

Run `brew install pyenv` to install PyEnv.

Post-installation, run `pyenv --version` to confirm the installation.

Next, we need to set up our shell environment for Pyenv.

For zsh Shell, run the following commands:

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```

For other shells, refer [this](https://github.com/pyenv/pyenv#set-up-your-shell-environment-for-pyenv) section

### 1b PyEnv Useful Commands

#### To install a version of Python

1. To do that, first, we need to check all the available versions of Python via `pyenv install --list`.
    
2. Run `pyenv install <version>` to install a particular version. E.g., `pyenv install 3.11.8` and `pyenv install 3.10.13`.
    

Let's install both of them.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🦂</div>
<div data-node-type="callout-text">Error Resolution</div>
</div>

If you see below error while installing 3.11.8

```plaintext
Traceback (most recent call last):

  File "<string>", line 1, in <module>In

  File "/Users/atech-guide/.pyenv/versions/3.11.8/lib/python3.11/lzma.py", line 27, in <module>
tppl
    from _lzma import *

ModuleNotFoundError: No module named '_lzma'
```

As solution, do the following

* Install xz =&gt; brew install xz
    
* un-install Python =&gt; pyenv uninstall 3.11.8
    
* reinstall Python =&gt; pyenv install 3.11.8
    

Post successful installation, let's list the Python versions via `pyenv versions`, we see the following:

```bash
atech.guide@macbook-air-m1 ~ % pyenv versions
* system (set by /Users/atech-guide/.pyenv/version)
  3.10.13
  3.11.8
```

Where `system` represents the Python that comes with MacBook.

#### To Use a version of Python in the current Folder

Run `pyenv local <version>`

#### To set a version of Python Globally

Run `pyenv global <version>`

E.g. `pyenv global 3.10.13`

#### To delete a version of Python

Run `pyenv uninstall <version>`

E.g. `pyenv uninstall 3.10.13`

### 1c PyEnv Example

Let's create a folder named `python_projects` .

Under it let's create two example projects, `example_python_project_1` and `example_python_project_2` .

At end, we have a folder structure as follows

```bash
atech.guide@macbook-air-m1 python_projects % tree
.
├── example_python_project_1
└── example_python_project_2
```

Under each project sub folder, lets use different versions of python by running

* `pyenv local 3.11.8` for example\_python\_project\_1
    
* `pyenv local 3.10.13` for example\_python\_project\_2
    

If we check the python versions under both the sub folders (via `python --version`) we will see different versions

```bash
atech.guide@macbook-air-m1 python_projects % cd example_python_project_1
atech.guide@macbook-air-m1 example_python_project_1 % pyenv local 3.11.8
atech.guide@macbook-air-m1 example_python_project_1 % python --version
Python 3.11.8

atech.guide@macbook-air-m1 example_python_project_1 % cd ../example_python_project_2

atech.guide@macbook-air-m1 example_python_project_2 % pyenv local 3.10.13      
atech.guide@macbook-air-m1 example_python_project_2 % python --version
Python 3.10.13
```

### 1d PyEnv Command Table

| Action | Command |
| --- | --- |
| To check versions and which python is activated | `pyenv versions` |
| To check Available versions | `pyenv install --list` |
| To install a version | `pyenv install 3.11.8` |
| Where is python installed | `ls ~/.pyenv/versions/` |
| Uninstalling Python | `pyenv uninstall 3.10.5` |
| Setting Global Python | `pyenv global 3.10.5` |
| Setting Local Python | `pyenv local 2.7.15` |
| Which python is activated in pyenv | `pyenv which python` |

This solves one part of the problem.

Another part is we need to create Isolated Environments for each Python Project.

For that, we will need another tool.

## 2 PyEnv Virtualenv

* It is a PyEnv plugin that provides features to manage virtualenvs for Python.
    

### 2a Installing PyEnv Virtualenv

Run `brew install pyenv-virtualenv` to install PyEnv

Next, we need to set up our shell environment for Pyenv Virtualenv.

For zsh Shell, run `echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc`.

### 2b PyEnv Virtualenv Useful Commands

#### To create a virtual env

Run `pyenv virtualenv <python_version> <environment_name>`.

#### To use virtual env

Run `pyenv local <my-virtual-env>`

#### To List virtual env

Run `pyenv virtualenvs`

#### To delete virtual env

Run `pyenv virtualenv-delete <my-virtual-env>`

E.g. `pyenv virtualenv-delete python_project-3.11`

### 2c PyEnv Virtualenv Example

Before Creating Virtual environment

```bash
atech.guide@macbook-air-m1 ~ % pyenv versions
* system (set by /Users/atech-guide/.pyenv/version)
  3.10.13
  3.11.8
```

Creating a Virtual Environment -&gt; `pyenv virtualenv 3.11.8 example_python_project_1`

```bash
atech.guide@macbook-air-m1 ~ % pyenv virtualenv 3.11.8 example_python_project_1 
atech.guide@macbook-air-m1 ~ % pyenv versions
* system (set by /Users/atech-guide/.pyenv/version)
  3.10.13
  3.11.8
  3.11.8/envs/example_python_project_1
  example_python_project_1 --> /Users/atech-guide/.pyenv/versions/3.11.8/envs/example_python_project_1
```

Where `3.11.8/envs/example_python_project_1` is virtual env and `example_python_project_1` is Symlink

### 2d PyEnv Virtualenv Command Table

| Action | Command |
| --- | --- |
| Create Virtual Env | `pyenv virtualenv <python_version> <environment_name>` |
| Use Virtual env | `pyenv local <environment_name>` |
| List virtual env | `pyenv virtualenvs` |
| Remove Virtual env | `pyenv virtualenv-delete <environment_name>` |

## Conclusion

In conclusion, installing Python on a MacBook doesn't have to be a daunting task.

By leveraging tools like PyEnv and PyEnv Virtualenv, we can easily manage multiple Python versions and create isolated environments for our projects.

This step-by-step guide has walked us through the process of setting up Python on your MacBook, via

1. Leveraging PyEnv to install multiple Python versions.
    
2. Creating and managing virtual environments with PyEnv Virtualenv
    

With these tools at our disposal, we can avoid common pitfalls such as version conflicts, environment pollution, and difficulty in replicating development environments, ensuring a smoother and more efficient workflow for our Python projects.

Remember, the key to mastering Python setup on your MacBook is practice and exploration, so don't hesitate to experiment with different versions and environments as you become more comfortable with these tools.

Next, we will learn how to set up a Python Project in my next Article.

## References

* [Homebrew](https://brew.sh)
    
* PyEnv [GitHub](https://github.com/pyenv/pyenv)
    
* PyEnv pyenv-virtualenv [GitHub](https://github.com/pyenv/pyenv-virtualenv)
    
* Python 3.11.8 installation error solution [Gist](https://gist.github.com/iandanforth/f3ac42b0963bcbfdf56bb446e9f40a33)
    
* Image Credit: Google Gemini