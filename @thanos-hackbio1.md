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

The conda configuration file, `.condarc` is an optional runtime configuration file that allows advanced users to configure various aspects of conda, such as which channels it searches for packages, proxy settings and environment directories.

The `.condarc` file is not included by default, but it is automatically created in your home directory the first time you run the `conda config` command.

A `.condarc` file may also be located in the root environment, in which case it overrides any in the home directory.

NOTE: A `.condarc` file can also be used in an administrator-controlled installation to override the users’ configuration
The `.condarc` configuration file follows simple [YAML syntax](https://docs.ansible.com/YAMLSyntax.html)

The `.condarc` file can change many parameters, including:

- Where conda looks for packages.
- If and how conda uses a proxy server.
- Where conda lists known environments.
- Whether to update the bash prompt with the current activated environment name.
- Whether user-built packages should be uploaded to Anaconda.org.
- Default packages or features to include in new environments.

To create or modify a `.condarc` file, use the `conda config` command or use a text editor to create a new file named .condarc and save it to your user home directory or root directory.

EXAMPLE:

> conda config --add channels conda-forge

You can also download a [sample .condarc file](https://docs.conda.io/projects/conda/en/4.6.1/user-guide/configuration/sample-condarc.html) to edit in your editor and save to your user home directory or root directory.

To set configuration options, edit the `.condarc` file directly or use the `conda config --set` command.

EXAMPLE: To set the auto_update_conda option to `False`, run:

> conda config --set auto_update_conda False

For a complete list of conda config commands, see the command reference. The same list is available at the Terminal or Anaconda Prompt by running `conda config --help`.

TIP: Conda supports [tab completion](https://docs.conda.io/projects/conda/en/4.6.1/user-guide/configuration/enable-tab-completion.html) with external packages instead of internal configuration.

## General configuration

### Channel locations (channels)

Listing channel locations in the `.condarc` file overrides conda defaults, causing conda to search only the channels listed here, in the order given.

Use `defaults` to automatically include all default channels. Non-URL channels are interpreted as Anaconda.org user names. You can change this by modifying the channel_alias as described in [Set a channel alias (channel_alias)](https://docs.conda.io/projects/conda/en/4.6.1/user-guide/configuration/use-condarc.html#set-ch-alias). The default is just `defaults`.

EXAMPLE:
> channels:
>   \- <anaconda_dot_org_username>
>   \- http://some.custom/channel
>   \- file:///some/local/directory
>   \- defaults

To select channels for a single environment, put a `.condarc` file in the root directory of that environment (or use the `--env` option when using `conda config`).

EXAMPLE: If you have installed Miniconda with Python 3 in your home directory and the environment is named “flowers”, the path may be:

> ~/miniconda3/envs/flowers/.condarc

### Allow other channels (allow_other_channels)

The system-level `.condarc` file may specify a set of allowed channels, and it may allow users to install packages from other channels with the boolean flag allow_other_channels. The default is `True`.

If allow_other_channels is set to `False`, only those channels explicitly specified in the system `.condarc` file are allowed:

> allow_other_channels: False

When allow_other_channels is set to `True` or not specified, each user has access to the default channels and to any channels that the user specifies in their local `.condarc` file. When allow_other_channels is set to `false`, if the user specifies other channels, the other channels are blocked, and the user receives a message reporting that channels are blocked. For more information, see [Example administrator-controlled installation.](https://docs.conda.io/projects/conda/en/4.6.1/user-guide/configuration/admin-multi-user-install.html#admin-inst)

If the system `.condarc` file specifies a channel_alias, it overrides any channel aliases set in a user’s `.condarc` file. See Set a channel alias (channel_alias).

### Default channels (default_channels)

Normally the defaults channel points to several channels at the [repo.continuum.io](https://repo.anaconda.com/) repository, but if default_channels is defined, it sets the new list of default channels. This is especially useful for air gap and enterprise installations:

> default_channels:
>   \- <anaconda_dot_org_username>
>   \- http://some.custom/channel
>   \- file:///some/local/directory

### Update conda automatically (auto_update_conda)

When `True`, conda updates itself any time a user updates or installs a package in the root environment. When `False`, conda updates itself only if the user manually issues a `conda update` command. The default is `True`.

EXAMPLE:

> auto_update_conda: False

### Always yes (always_yes)

Choose the `yes` option whenever asked to proceed, such as when installing. Same as using the `--yes` flag at the command line. The default is `False`.

EXAMPLE:

> always_yes: True

### Show channel URLs (show_channel_urls)

Show channel URLs when displaying what is going to be downloaded and in `conda list`. The default is `False`.

EXAMPLE:

> show_channel_urls: True

### Change command prompt (changeps1)

When using `activate`, change the command prompt from `$PS1` to include the activated environment. The default is `True`.

EXAMPLE:

> changeps1: False

### Add pip as Python dependency (add_pip_as_python_dependency)

Add pip, wheel and setuptools as dependencies of Python. This ensures that pip, wheel and setuptools are always installed any time Python is installed. The default is `True`.

EXAMPLE:

> add_pip_as_python_dependency: False

### Use pip (use_pip)

Use pip when listing packages with `conda list`. This does not affect any conda command or functionality other than the output of the command `conda list`. The default is `True`.

EXAMPLE:

> use_pip: False

### Configure conda for use behind a proxy server (proxy_servers)

By default, proxy settings are pulled from the HTTP_PROXY and HTTPS_PROXY environment variables or the system. Setting them here overrides that default:

> proxy_servers:
>   http: http://user:pass@corp.com:8080
>   https: http://user:pass@corp.com:8080

To give a proxy for a specific scheme and host, use the scheme://hostname form for the key. This matches for any request to the given scheme and exact host name:

> proxy_servers:
>   'http://10.20.1.128': 'http://10.10.1.10:5323'

If you do not include the user name and password or if authentication fails, conda prompts for a user name and password.

If your password contains special characters, you need escape them as described in [Percent-encoding reserved characters](https://en.wikipedia.org/wiki/Percent-encoding#Percent-encoding_reserved_characters) , on Wikipedia.

Be careful not to use `http` when you mean https or `https` when you mean http.

### SSL verification (ssl_verify)

If you are behind a proxy that does SSL inspection such as a Cisco IronPort Web Security Appliance (WSA), you may need to use ssl_verify to override the SSL verification settings.

By default this variable is `True`, which means that SSL verification is used and conda verifies certificates for SSL connections. Setting this variable to `False` disables the connection’s normal security and is not recommended:

> ssl_verify: False

You can also set ssl_verify to a string path to a certificate, which can be used to verify SSL connections:

> ssl_verify: corp.crt

### Offline mode only (offline)

Filters out all channel URLs that do not use the `file://` protocol. The default is `False`.

EXAMPLE:

> offline: True

For advanced set-up or configurations, visit <https://docs.conda.io/projects/conda/en/4.6.1/user-guide/configuration/use-condarc.html#advanced-configuration>