# Texdoc 3.3 (2021-03-17)

[![Build Status](https://travis-ci.org/TeX-Live/texdoc.svg?branch=master)](https://travis-ci.org/TeX-Live/texdoc)
[![Build status](https://ci.appveyor.com/api/projects/status/uq28ms7eba7ns6d3/branch/master?svg=true)](https://ci.appveyor.com/project/wtsnjp/texdoc/branch/master)

Texdoc is a command line program to find and view documentation in TeX Live.

## General Information

* Website: <https://www.tug.org/texdoc/>
* Repository: <https://github.com/TeX-Live/texdoc/>
* Mailing list: <texdoc@tug.org>

## Using Texdoc

Texdoc is part of the TeX Live distribution. Generally, you don't have to install it yourself.

If you want to try/test the develop version, please see below.

## How to Install the Develop Version

### Using Bundler

The easiest way to install the develop version of Texdoc is using [Bundler](https://bundler.io/) and [Rake](https://github.com/ruby/rake):

```
$ bundle install
$ rake install
```

If you want to uninstall the develop version (to use the TeX Live version), just try:

```
$ rake uninstall
```

### Installing manually

Here, `$TEXDOC` means the path to the texdoc dev sources you cloned (or downloaded), and `$TEXMFHOME` denotes your personal TEXMF tree (you can get its location with `kpsewhich --var-value TEXMFHOME`).

* **The command.** Symlink or copy `$TEXDOC/script` as `$TEXMFHOME/scripts/texdoc`.
* **The configuration file.** Symlink or copy `$TEXDOC/texdoc.cnf` as `$TEXMFHOME/texdoc/texdoc-dist.cnf` (notice the `-dist` part). It will completely override the other configuration files except `$TEXMFHOME/texdoc/texdoc.cnf` which you can still use for you personal settings.

You can make sure that the right files are used by running `texdoc --files`: the first line contains the full path to the version of used `texdoclib.tlu`, and the rest lists the configuration files in use.

## Files in This Repository

- `doc/` contains the documentation,
- `script/` contains the source code,
- `spec/` is a directory for testing scripts, and
- `texdoc.cnf` is the default configuration file.

## Building and Testing

Many building tasks are defined as [Rake](https://github.com/ruby/rake) tasks:

### Generating all documentation

The following will generate both the PDF and the manpage in `doc/` directory.

```
$ rake doc
```

### Generating a pre-hashed cache file

The following will generate a pre-hashed cache file `script/Data.tlpdb.lua`. This task have to be done under a TeX Live setup with tlpdb.

```
$ rake gen_datafile
```

### Running tests

The following will run all tests in `spec/` directory.

```
$ rake test
```

Alternatively, you can give spec names with the `--list` (`-l`) option for this task. E.g., following will run only `spec/action/help_spec.rb` and `spec/mode/list_spec.rb`:

```
$ rake test -- -l action/help,mode/list
```

### Showing all available tasks

Following will show all available tasks with a short description.

```
$ rake -T
```

In addition to that, for options available tasks, e.g., `rake test` and `rake run_texdoc`, you can get options information with `-h` option for each task:

```
$ rake test -- -h
```

## Further Information

More specific information, such as the TODO list of this project and some information for distributors, can be found in the Wiki of our GitHub repository. Please visit:

* <https://github.com/TeX-Live/texdoc/wiki>

## Copyright and License

Copyright 2008-2021 Manuel Pégourié-Gonnard, Takuto Asakura, the TeX Live Team.

This package is distributed under the terms of the GNU General Public License as published by the Free Software Foundation, either [version 3](./COPYING) of the License, or (at your option) any later version.

Previous work (texdoc program) in the public domain:

* Contributions from Reinhard Kotucha (2008).
* First texlua versions by Frank Küster (2007).
* Original shell script by Thomas Esser, David Aspinall, and Simon Wilkinson.
