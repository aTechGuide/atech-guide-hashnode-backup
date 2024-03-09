---
title: "Beginners essential Guide to Setting Up Python on a MacBook in 2024"
slug: beginners-essential-guide-to-setting-up-python-on-a-macbook-in-2024

---

## **Can You Relate?**

👉 You want a step-by-step guide to install Python on MacBook

👉 You have faced ***Version Conflicts*** i.e. Different projects may require different Python versions, leading to conflicts and difficulties in managing the appropriate version for each project.

👉 You have faced ***Environment Pollution*** i.e. Installing various packages globally can pollute the global namespace, leading to issues where one project's dependencies interfere with another's.

👉 You have faced ***Difficulty in Replication*** i.e. Setting up an identical development environment on a different machine becomes cumbersome, as it requires manually ensuring the same versions of Python and all dependencies are installed.

👉 You have faced ***Risk of Breaking the System*** where Installing and uninstalling packages globally can potentially lead to system-wide issues, especially if critical system dependencies are accidentally removed or overwritten.

If the answer is “yes” to any of the above,  

Read this page carefully

## Pre Requisites

* Macbook
    
* Homebrew Installation
    

> Homebrew for Mac is a free and open-source software package management system that simplifies the installation of software on macOS and Linux

Installation Command

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Let's being installing the Python on Mac via

## PyEnv

* This tool helps in installing and easily switching between multiple versions of Python
    
* We can set *Global Python* version on per user basis
    
* We can set *Per Project* Python versions\\
    

### Installing PyEnv

```bash
brew install pyenv
```

Post Installation, we can check the installation via

```bash
pyenv --version
```

### PyEnv Useful command

#### To list all the Python Versions available to PyEnv

Run `pyenv versions`

At the beginning you will see the following

```bash
➜  ~ pyenv versions
* system (set by /Users/bornshrewd/.pyenv/version)
```

This displays the Python that comes with MacBook

#### To List all available versions of Python

Run `pyenv install --list`

#### To install a versions of Python

Run `pyenv install <version>`

E.g. `pyenv install 3.11.8` and `pyenv install 3.10.13`

Let's install both of them, On listing the available Python versions via `pyenv versions` we see the following

#### To un install a versions of Python

Run `pyenv uninstall <version>`

E.g. `pyenv uninstall 3.10.13`

#### To set a versions of Python in current Folder

Run `pyenv local <version>`

E.g. `pyenv local 3.10.13`

It creates a `.python-version` file in your current directory

#### To set a versions of Python Globally

Run `pyenv global <version>`

E.g. `pyenv global 3.10.13`

### PyEnv Command Table

<table><tbody><tr><td colspan="1" rowspan="1"><p>To check versions and which python is activated</p></td><td colspan="1" rowspan="1"><p>pyenv versions</p></td></tr><tr><td colspan="1" rowspan="1"><p>To check Available versions</p></td><td colspan="1" rowspan="1"><p>pyenv install --list | grep " 3.11"</p></td></tr><tr><td colspan="1" rowspan="1"><p>To install a version</p></td><td colspan="1" rowspan="1"><p>pyenv install 3.11.8</p></td></tr><tr><td colspan="1" rowspan="1"><p>Where is python installed</p></td><td colspan="1" rowspan="1"><p>ls ~/.pyenv/versions/</p></td></tr><tr><td colspan="1" rowspan="1"><p>Uninstalling Python</p></td><td colspan="1" rowspan="1"><p>pyenv uninstall 3.10.5</p></td></tr><tr><td colspan="1" rowspan="1"><p>Setting Global Python</p></td><td colspan="1" rowspan="1"><p>pyenv global 3.10.5</p></td></tr><tr><td colspan="1" rowspan="1"><p>Setting Local Python</p></td><td colspan="1" rowspan="1"><p>pyenv local 2.7.15</p></td></tr><tr><td colspan="1" rowspan="1"><p>Which python is activated in pyenv</p></td><td colspan="1" rowspan="1"><p>pyenv which python</p></td></tr></tbody></table>

This solves one part of the problem.

The another part is we need to create Isolated Environments for each Python Project.

For that we will need another tool

## Pyenv Virtualenv

## References

* [Homebrew](https://brew.sh)
    
* PyEnv [Github](https://github.com/pyenv/pyenv)