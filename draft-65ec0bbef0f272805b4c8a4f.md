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

Let's install both of them

## References

* [Homebrew](https://brew.sh)
    
* PyEnv [Github](https://github.com/pyenv/pyenv)