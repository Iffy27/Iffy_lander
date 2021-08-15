# LINUX BASED INSTRUCTIONS TO INSTALL AND SETUP CONDA ENVIRONMENT

Conda is a powerful package manager and environment manager that you use with command line commands at the Anaconda Prompt for Windows, or in a Terminal window for macOS or Linux.

## Installation

The fastest way to obtain conda is to install Miniconda, a mini version of Anaconda that includes only conda and its dependencies. If you prefer to have conda plus over 720 open source packages, install Anaconda.

We recommend you install Anaconda for the local user, which does not require administrator permissions and is the most robust type of installation. You can also install Anaconda system wide, which does require administrator permissions.


### Installing on linux

1. Dowunload the installer:
- [Miniconda installer for linux](https://docs.conda.io/en/latest/miniconda.html)
- [Anaconda installer for linux](https://www.anaconda.com/products/individual)

2. In your Terminal window, run:
- Miniconda:
> bash Miniconda3-latest-Linux-x86_64.sh

- Anaconda:
> bash Anaconda-latest-Linux-x86_64.sh

3. Follow the prompts on the installer screens.

If you are unsure about any setting, accept the defaults. You can change them later.

4. To make the changes take effect, close and then re-open your Terminal window.

5. [Test your installations](https://docs.conda.io/projects/conda/en/4.6.1/user-guide/install/test-installation.html)

# Configuration

## Using the .condarc conda configuration file

The conda configuration file, > .condarc, is an optional runtime configuration file that allows advanced users to configure various aspects of conda, such as which channels it searches for packages, proxy settings and environment directories.

The > .condarc file is not included by default, but it is automatically created in your home directory the first time you run the > conda config command.

A > .condarc file may also be located in the root environment, in which case it overrides any in the home directory.

NOTE: A > .condarc file can also be used in an administrator-controlled installation to override the users’ configuration
