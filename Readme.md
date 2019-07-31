# Minimal gn project


# Purpose of this project

To understand, how
[`gn`](https://gn.googlesource.com/gn/)
,the _generate Ninja_ Meta Build System, works, I found it useful to set up a very basic project.

This has been done before, e.g.
[here](https://github.com/skopf/minimal-gn-project),
but there, templates from existing projects were used.
They make `gn` much more usable, because they already contain a lot of effort to let `gn` work under different conditions (e.g. different platforms), but are not easy to understand.
The sparse documentation of `gn` is not really helping there, either.


# Notes on `gn`

See [`gn.md`](gn.md).


# Tested on

This project was tested on Arch Linux with at least `gn`, `ninja` and `gcc` installed.
