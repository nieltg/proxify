# Proxify

`proxify` is a script for configuring proxy in most command-line tools. It works
by setting `http_proxy` and other related environment variables and pass them to
specified command.

## Installation

`proxify` is best if it is installed at the system because priviledge escalation
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
Authentificate? [Y/N] y
User: nieltansah
Pass:
Already up-to-date.
```

For escalated commands, `proxify` shall be specified to be escalated too because
priviledge escalation tools, like `sudo` discard some environment variables from
user. For example:

```sh
$ sudo proxify apt-get install zsh
```
