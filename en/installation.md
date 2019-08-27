# Installing Nu

The best way currently to get Nu up and running is to install either from [crates.io](https://crates.io) or to build it from source. 

## Getting Ready

Before we can install Nu, we need to make sure our system has the necessary requirements. Currently, this means making sure we have both the Rust toolchain and local dependencies installed.

### Installing Rust

If we don't already have Rust on our system, the best way to install it via [rustup](https://rustup.rs/). Rustup is a way of managing Rust installations, including managing using different Rust versions. 

Nu currently requires the **nightly** version of Rust. When you first open "rustup" it will ask what version of Rust you wish to install:

```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

Select option #2 to customize the installation, 

```
Default host triple?
```

Hit enter here to select the default.

```
Default toolchain? (stable/beta/nightly/none)
```

Make sure to type "nightly" here and press enter. This should give this setup:

```
Modify PATH variable? (y/n)
```

You can optionally update your path. This is generally a good idea, as it makes later steps easier.


```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: nightly
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

You can see that our default toolchain has now changed to the nightly toolchain. If this sounds a bit risky, don't worry. The Rust compiler is run through a full battery of tests. The nightly compiler is often as reliable as the stable version.

Once we are ready, we press 1 and then enter.  After this point, we can follow the instructions "rustup" gives us and we should have a working Rust compiler on our system.

If you'd rather not install Rust via "rustup", you can also install it via other methods (eg from a package in a Linux distro). Just be sure to install a recent nightly version of the toolchain.

## Dependencies

### Debian/Ubuntu

You will need to install the "libssl-dev" package:

```
apt install libssl-dev
```

Linux users who wish to use the `rawkey` or `clipboard` optional features will need to install the "libx11-dev" and "libxcb-composite0-dev" packages:

```
apt install libxcb-composite0-dev libx11-dev
```

### macOS

Using [homebrew](https://brew.sh/), you will need to install the "openssl" formula:

```
brew install openssl
```

## Installing from [crates.io](https://crates.io)

Once we have the dependencies Nu needs, we can install it using the `cargo` command that comes with the Rust compiler.

```
> cargo install nu
```

That's it!  The cargo tool will do the work of downloading Nu and its source dependencies, building it, and installing it into the cargo bin path so that we can run it.

Once installed, we can run Nu using the `nu` command:

```
$ nu
/home/jonathan/Source> 
```

## Building from source

We can also build our own Nu from source directly from github. This gives us immediate access to the latest Nu features and bugfixes.

```
> git clone https://github.com/nushell/nushell.git
```

Git will clone the main nushell repo for us. From there, we can build and run Nu:

```
> cd nushell
nushell> cargo build && cargo run
```

You can also build and run Nu in release mode:

```
nushell> cargo build --release && cargo run --release
```

People familiar with Rust may wonder why we do both a "build" and a "run" step if "run" does a build by default. This is to get around a shortcoming of the new `default-run` option in Cargo, and ensure that all plugins are built, though this may not be required in the future.

