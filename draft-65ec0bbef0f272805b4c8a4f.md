---
title: "Step-by-Step Guide: Installing Python on a MacBook for Beginners (2024 Edition)"
slug: beginners-essential-guide-to-setting-up-python-on-a-macbook

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

### Homebrew Installation

We can install Homebrew via following command

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Let's begin installing Python on Mac via.

## 1 PyEnv

* This tool helps in installing and easily switching between multiple versions of Python
    
* We can set *Global Python* version on per user basis
    
* We can set *Per Project* Python versions\\
    

### 1a Installing PyEnv

Run `brew install pyenv` to Install PyEnv

Post installation, Run `pyenv --version` to confirm the installation.

Next, we need to set up our shell environment for Pyenv

For zsh Shell, run following commands

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```

For other shells, refer [this](https://github.com/pyenv/pyenv#set-up-your-shell-environment-for-pyenv) section

### 1b PyEnv Useful command

#### To install a version of Python

1. To do that, first we need to check all the available versions of Python via `pyenv install --list`
    
2. Run `pyenv install <version>` to install a particular version. E.g. `pyenv install 3.11.8` and `pyenv install 3.10.13`
    

Let's install both of them

On listing the available Python versions via `pyenv versions` we see the following

```bash
➜  ~ pyenv versions                        
* system (set by /Users/bornshrewd/.pyenv/version)
  3.10.13
  3.11.8
```

Where `system` represents the Python that comes with MacBook

#### To Use a version of Python in current Folder

Run `pyenv local <version>`

E.g.

1. Let's create a `temp` folder and run `pyenv local 3.10.13` inside it
    
2. It will create a `.python-version` file in the current directory
    
3. On running `python --version` we will see `Python 3.10.13`
    

```bash
➜  ~ cd temp 
➜  temp pyenv local 3.10.13
➜  temp ls -a              
.               ..              .python-version
➜  temp cat .python-version 
3.10.13
➜  temp python --version
Python 3.10.13
```

#### To set a version of Python Globally

Run `pyenv global <version>`

E.g. `pyenv global 3.10.13`

#### To delete a version of Python

Run `pyenv uninstall <version>`

E.g. `pyenv uninstall 3.10.13`

### 1c PyEnv Command Table

<table><tbody><tr><td colspan="1" rowspan="1"><p>To check versions and which python is activated</p></td><td colspan="1" rowspan="1"><p>pyenv versions</p></td></tr><tr><td colspan="1" rowspan="1"><p>To check Available versions</p></td><td colspan="1" rowspan="1"><p>pyenv install --list | grep " 3.11"</p></td></tr><tr><td colspan="1" rowspan="1"><p>To install a version</p></td><td colspan="1" rowspan="1"><p>pyenv install 3.11.8</p></td></tr><tr><td colspan="1" rowspan="1"><p>Where is python installed</p></td><td colspan="1" rowspan="1"><p>ls ~/.pyenv/versions/</p></td></tr><tr><td colspan="1" rowspan="1"><p>Uninstalling Python</p></td><td colspan="1" rowspan="1"><p>pyenv uninstall 3.10.5</p></td></tr><tr><td colspan="1" rowspan="1"><p>Setting Global Python</p></td><td colspan="1" rowspan="1"><p>pyenv global 3.10.5</p></td></tr><tr><td colspan="1" rowspan="1"><p>Setting Local Python</p></td><td colspan="1" rowspan="1"><p>pyenv local 2.7.15</p></td></tr><tr><td colspan="1" rowspan="1"><p>Which python is activated in pyenv</p></td><td colspan="1" rowspan="1"><p>pyenv which python</p></td></tr></tbody></table>

This solves one part of the problem.

The another part is we need to create Isolated Environments for each Python Project.

For that we will need another tool

## 2 PyEnv Virtualenv

* It is a PyEnv plugin that provides features to manage virtualenvs for Python
    

### 2a Installing PyEnv Virtualenv

Run `brew install pyenv-virtualenv` to Install PyEnv

Next, we need to set up our shell environment for Pyenv Virtualenv

For zsh Shell, Run `echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc`

### 2b PyEnv Virtualenv Useful command

#### To create a virtual env

Run `pyenv virtualenv <python_version> <environment_name>`

Example

* Before Creating Virtual environment
    

```bash
➜  ~ pyenv versions
* system (set by /Users/bornshrewd/.pyenv/version)
  3.10.13
  3.11.8
```

* Creating a Virtual Environment -&gt; `pyenv virtualenv 3.11.8 python_project-3.11`
    
* Post Creating Virtual Environment, I can see `3.11.8/envs/python_project-3.11` and a Symlink `python_project-3.11`
    
    * I can
        

```bash
➜  ~ pyenv virtualenv 3.11.8 python_project-3.11 
➜  ~ pyenv versions                              
* system (set by /Users/bornshrewd/.pyenv/version)
  3.10.13
  3.11.8
  3.11.8/envs/python_project-3.11
  python_project-3.11 --> /Users/bornshrewd/.pyenv/versions/3.11.8/envs/python_project-3.11
```

#### To use virtual env

Run `pyenv local <my-virtual-env>`

E.g.

* Create a Project `python_project-3.11`
    
* Use virtual env `pyenv local python_project-3.11`
    

```bash
➜  ~ mkdir python_project-3.11
➜  ~ cd python_project-3.11
➜  python_project-3.11 pyenv local python_project-3.11
(python_project-3.11) ➜  python_project-3.11 ls -a
.               ..              .python-version
(python_project-3.11) ➜  python_project-3.11 cat .python-version 
python_project-3.11
```

#### To List virtual env

Run `pyenv virtualenvs`

#### To delete virtual env

Run `pyenv virtualenv-delete <my-virtual-env>`

E.g. `pyenv virtualenv-delete python_project-3.11`

### 2c PyEnv Virtualenv Command Table

<table><tbody><tr><td colspan="1" rowspan="1"><p>Create Virtual Env</p></td><td colspan="1" rowspan="1"><p>pyenv virtualenv &lt;python_version&gt; &lt;environment_name&gt;</p></td></tr><tr><td colspan="1" rowspan="1"><p>Use Virtual env</p></td><td colspan="1" rowspan="1"><p>pyenv local &lt;environment_name&gt;</p></td></tr><tr><td colspan="1" rowspan="1"><p>List virtual env</p></td><td colspan="1" rowspan="1"><p>pyenv virtualenvs</p></td></tr><tr><td colspan="1" rowspan="1"><p>Remove Virtual env</p></td><td colspan="1" rowspan="1"><p>pyenv virtualenv-delete &lt;environment_name&gt;</p></td></tr></tbody></table>

## Conclusion

In conclusion, installing Python on a MacBook doesn't have to be a daunting task.

By leveraging tools like PyEnv and PyEnv Virtualenv, we can easily manage multiple Python versions and create isolated environments for our projects.

This step-by-step guide has walked us through the process of setting up Python on your MacBook, via

1. Leveraging PyEnv to install multiple Python Versions
    
2. Creating and managing virtual environments with PyEnv Virtualenv
    

With these tools at our disposal, we can avoid common pitfalls such as version conflicts, environment pollution, and difficulty in replicating development environments, ensuring a smoother and more efficient workflow for our Python projects.

Remember, the key to mastering Python setup on your MacBook is practice and exploration, so don't hesitate to experiment with different versions and environments as you become more comfortable with these tools.

Next, we will learn how to set up Python Project in my next Article.

## References

* [Homebrew](https://brew.sh)
    
* PyEnv [Github](https://github.com/pyenv/pyenv)
    
* PyEnv pyenv-virtualenv [Github](https://github.com/pyenv/pyenv-virtualenv)