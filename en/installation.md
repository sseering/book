---
layout: content
title: Installing Nu
prev: Table of Contents
next: Introduction
link_prev: /en/table_of_contents.html
link_next: /en/introduction.html
---

The best way currently to get Nu up and running is to install from [crates.io](https://crates.io), download pre-built binaries from our [release page](https://github.com/nushell/nushell/releases), build from source, or pulling a pre-built container with Docker.

## Pre-built binaries

You can download Nu pre-built from the [release page](https://github.com/nushell/nushell/releases). Alternatively, if you use [Homebrew](https://brew.sh/) for macOS, you can install the binary by running `brew install nushell`.

### Windows

**please note:** Nu works on Windows 10 and does not currently have Windows 7/8.1 support.

Download the current released `.zip`-file from the [release page](https://github.com/nushell/nushell/releases) and extract it for example to:

```
C:\Program Files
```

And then add the folder of `nu` to your PATH. Once we have done that, we can run Nu using the `nu` command:

```
> nu
C:\Users\user>
```



If you are using the new [Windows Terminal](https://github.com/microsoft/terminal) you can set `nu` as your default shell by adding:

```         
            {
            "guid": "{2b372ca1-1ee2-403d-a839-6d63077ad871}",
            "hidden": false,
            "name": "Nu Shell",
            "commandline": "nu.exe"
            }
```

to  `"profiles"` in your Terminal Settings (JSON-file). The last thing to do is to change the `"defaultProfile"` to:

```
"defaultProfile": "{2b372ca1-1ee2-403d-a839-6d63077ad871}",
```

Now `nu` should load on startup of the Windows Terminal.

## Pre-built docker containers

If you want to pull a pre-built container, you can browse tags for the [nushell organization](https://quay.io/organization/nushell)
on Quay.io. Pulling a container would come down to:

```bash
$ docker pull quay.io/nushell/nu
$ docker pull quay.io/nushell/nu-base
```

Both "nu-base" and "nu" provide the `nu` binary, however nu-base also includes the source code at `/code`
in the container and all dependencies.

Optionally, you can also build the containers locally using the [dockerfiles provided](https://github.com/nushell/nushell/tree/master/docker):
To build the base image:

```bash
$ docker build -f docker/Dockerfile.nu-base -t nushell/nu-base .
``` 

And then to build the smaller container (using a Multistage build):

```bash
$ docker build -f docker/Dockerfile -t nushell/nu .
``` 

Either way, you can run either container as follows:

```bash
$ docker run -it nushell/nu-base
$ docker run -it nushell/nu
/> exit
```

The second container is a bit smaller, if size is important to you.

## Getting Ready

Before we can install Nu, we need to make sure our system has the necessary requirements. Currently, this means making sure we have both the Rust toolchain and local dependencies installed.

### Installing a compiler suite

For Rust to work properly, you'll need to have a compatible compiler suite installed on your system. These are the recommended compiler suites:

* Linux: GCC or Clang
* macOS: Clang (install Xcode)
* Windows: [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/)

For Linux and macOS, once you have installed the compiler, you are ready to install Rust via `rustup` (see below).

For Windows, when you install Visual Studio Community Edition, make sure to install the "C++ build tools" as what we need is `link.exe` which is provided as part of that optional install.  With that, we're ready to move to the next step.

### Installing Rust

If we don't already have Rust on our system, the best way to install it via [rustup](https://rustup.rs/). Rustup is a way of managing Rust installations, including managing using different Rust versions. 

Nu currently requires the **latest stable (1.43 or later)** version of Rust. The best way to let `rustup` find the correct version for you. When you first open `rustup` it will ask what version of Rust you wish to install:

```
Current installation options:

default host triple: x86_64-unknown-linux-gnu
default toolchain: stable
profile: default
modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

Once we are ready, we press 1 and then enter.

If you'd rather not install Rust via `rustup`, you can also install it via other methods (e.g. from a package in a Linux distro). Just be sure to install a version of Rust that is 1.39 or later.

## Dependencies

### Debian/Ubuntu

You will need to install the "pkg-config" and "libssl-dev" package:

```
apt install pkg-config libssl-dev
```

Linux users who wish to use the `rawkey` or `clipboard` optional features will need to install the "libx11-dev" and "libxcb-composite0-dev" packages:

```
apt install libxcb-composite0-dev libx11-dev
```

### RHEL

You'll need to install "libxcb", "libssl-dev", and "lib11-dev".

### macOS

Using [Homebrew](https://brew.sh/), you will need to install the "openssl" and "cmake" using: 

```
brew install openssl cmake
```

## Installing from [crates.io](https://crates.io)

Once we have the dependencies Nu needs, we can install it using the `cargo` command that comes with the Rust compiler.

```
> cargo install nu
```

That's it!  The cargo tool will do the work of downloading Nu and its source dependencies, building it, and installing it into the cargo bin path so that we can run it.

If you want to install with more features, you can use:

```
> cargo install nu --features=stable
```

For all the available features, the easiest way is to check out Nu and build it yourself using the same Rust tools:

```
> git clone https://github.com/nushell/nushell.git
> cd nushell
nushell> cargo install --path . --force --features=stable
```

For this to work, make sure you have all the dependencies (shown above) on your system.

Once installed, we can run Nu using the `nu` command:

```
$ nu
/home/jonathan/Source> 
```

## Building from source

We can also build our own Nu from source directly from github. This gives us immediate access to the latest Nu features and bug fixes.

```
> git clone https://github.com/nushell/nushell.git
```

Git will clone the main nushell repo for us. From there, we can build and run Nu if we are using `rustup` with:

```
> cd nushell
nushell> cargo build --workspace --features=stable && cargo run --features=stable
```

You can also build and run Nu in release mode:

```
nushell> cargo build --release --workspace --features=stable && cargo run --release --features=stable
```

People familiar with Rust may wonder why we do both a "build" and a "run" step if "run" does a build by default. This is to get around a shortcoming of the new `default-run` option in Cargo, and ensure that all plugins are built, though this may not be required in the future.

## Setting as your login shell

**!!! Nu is still in development, and may not be stable for everyday use. !!!**

To set the login shell you can use the [`chsh`](https://linux.die.net/man/1/chsh) command.
Some Linux distributions have a list of valid shells located in `/etc/shells` and will disallow changing the shell until Nu is in the whitelist. You may see an error similar to the one below if you haven't updated the `shells` file:

```
chsh: /home/username/.cargo/bin/nu is an invalid shell
```

You can add Nu to the list of allowed shells by appending your Nu binary to the `shells` file.
The path to add can be found with the command `which nu`, usually it is `$HOME/.cargo/bin/nu`.
