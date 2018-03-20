# Proxify

`proxify` is a script for configuring proxy in most command-line tools. It works
by setting `http_proxy` and other related environment variables and pass them to
specified command.

## Installation

`proxify` is best if it is installed at the system because privilege escalation
tools, like `sudo` prohibit some environment variables to be passed to escalated
command for some security reasons.

First, check `PATH` environment variable in escalated environment by:

```sh
$ sudo sh -c "echo \$PATH"
```

Then, install `proxify` script to one of specified directories. `/usr/local/bin`
is recommended to use.

```sh
$ sudo install -m 755 proxify /usr/local/bin
```

## Usage

`proxify` can be used by specifying commands after `proxify`. For example:

```sh
$ proxify git pull
Host: cache.itb.ac.id
Port: 8080
Authenticate? [Y/N] y
User: nieltansah
Pass:
Already up-to-date.
```

For escalated commands, `proxify` shall be specified to be escalated too because
privilege escalation tools, like `sudo` discard some environment variables from
user. For example:

```sh
$ sudo proxify apt-get install zsh
```

If you want `proxify` to prompt you for password only, you can use *proxify.conf* to store some configurations for you. First, open *proxify.conf*, and fill it with your desired configurations.

```conf
# Do not change the configuration name, only change the values instead.
# All leading and trailing whitespaces in configuration values will be ignored.

HOST=cache.itb.ac.id
PORT=8080
USER=nieltansah
```

When you are done, copy *proxify.conf* to your home directory as *.profixy.conf*.

```sh
$ cp proxify.conf ~/.proxify.conf
```

Whenever this file exists, `proxify` will use it as default configurations.