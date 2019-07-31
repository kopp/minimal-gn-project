# gn

Google's Meta Build System, generating for Ninja.
See [the project site](https://gn.googlesource.com/gn/).


# Language

- Comments: `#`


# Example

A not-quite minimal example is [here](https://github.com/skopf/minimal-gn-project) -- it uses some build configuration of the chromium project.
Really minimal but not really feature-rich example is [here](https://github.com/kopp/minimal-gn-project) -- it is totally un-portable and vary basic.


# Describe Build

- Root folder is marked by `.gn` file, see `gn help dotfile`.
- The `.gn` file contains at least `buildconfig` -- the path to the _build configuration file_,
  normally,
  [this file](https://chromium.googlesource.com/chromium/src/build.git/+/refs/heads/master/config/BUILDCONFIG.gn)
  is used, by adding
  [this repo](https://chromium.googlesource.com/chromium/src/build.git)
  as `build` folder.
  It defines build flags, and the toolchain to use through `set_default_toolchain()`.
- The toolchains is a path of a `BUILD.gn` file, e.g.
  [this for linux](https://chromium.googlesource.com/chromium/src/build.git/+/refs/heads/master/toolchain/linux/BUILD.gn).
  This at some point calls `toolchain()`, which calls `tool()` for each tool
  needed in the compilation steps; see `gn help tool` for a list of tools.
  See that help text also for a bunch of available variables which will be
  expanded like `{{source}}`.
  - NOTE: an invalid variable expansion, e.g. using `{{source}}` in `tool("link")` will fail with the error `Unknown tool type tool("link")`, which is totally not the actual problem...
  - NOTE: the first value of `outputs` will be available as `{{output}}`, so it's necessary to add something useful in there.
- Configured by `BUILD.gn` files.


# Run build

Generate the ninja files

    gn gen /tmp/asdf

and then run `ninja` on them

    ninja -C /tmp/asdf
