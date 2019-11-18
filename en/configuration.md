# Configuration

Nu has a small, but growing, number of internal variables you can set to change how it looks and how it operates.  Below is a list of the current variables, their types, and a description of how they're used

| Variable        | Type           | Description  |
| ------------- | ------------- | ----- |
| path | table of strings | PATH to use to find binaries |
| env | row | the environment variables to pass to external commands |
| ctrlc_exit | boolean | whether or not to exit Nu after multiple ctrl-c presses |
| table_mode | "light" or other | enable lightweight or normal tables |
| edit_mode | "vi" or "emacs" | changes line editing to "vi" or "emacs" mode |

## Usage

To set one of these variables, you can use `config --set`. For example:

```
> config --set [edit_mode "vi"]
```

## Configuring Nu as a login shell

To use Nu as a login shell, you'll need to configure the `path` and `env` configuration variables. With these, you'll have enough support to run external commands as a login shell.

Before switching, run Nu inside of another shell, like Bash. Then, take the environment and PATH from that shell with the following commands:
```
> config --set [path $nu:path]
> config --set [env $nu:env]
```

The `$nu:path` and `$nu:env` are special variables which are set to the current PATH and environment variables, respectively. Once you set these into the configuration, they'll be available later when using Nu as a login shell.

Next, on some distros you'll also need to ensure Nu is in the /etc/shells list:

```
❯ cat /etc/shells
# /etc/shells: valid login shells
/bin/sh
/bin/dash
/bin/bash
/bin/rbash
/usr/bin/screen
/usr/bin/fish
/home/jonathan/.cargo/bin/nu
```

With this, you should be able to `chsh` and set Nu to be your login shell. After a logout, on your next login you should be greeted with a shiny Nu prompt.

## Prompt configuration

Currently, prompt configuration is handled by installing Nu with the [starship](https://github.com/starship/starship) prompt support. 

```
nushell on 📙 master [$] is 📦 v0.5.1 via 🦀 v1.40.0-nightly 
❯ 
```

Starship is a fun, colorful, and surprisingly powerful prompt. To configure it, follow the steps in their [configuration manual](https://starship.rs/config/).
