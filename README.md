# Flycheck support for MMark

[![License GPL 3](https://img.shields.io/badge/license-GPL_3-green.svg)](http://www.gnu.org/licenses/gpl-3.0.txt)
[![MELPA](https://melpa.org/packages/flycheck-mmark-badge.svg)](https://melpa.org/#/flycheck-mmark)
[![Build Status](https://travis-ci.org/hasky-mode/flycheck-mmark.svg?branch=master)](https://travis-ci.org/hasky-mode/flycheck-mmark)

This package provides a [Flycheck](http://www.flycheck.org) checker for
[MMark](https://github.com/mmark-md/mmark) markdown processor.

## Installation

Download this package and place it somewhere, so Emacs can see it. Then put
`(require 'flycheck-mmark)` into your configuration file. Done!

TODO: mention MELPA once the package is there.

## Usage

First of all, build the [`mmark-cli`](https://github.com/mmark-md/mmark-cli)
executable and place it on your `PATH`. The easiest way to do that is
currently the following:

```
$ git clone https://github.com/mmark-md/mmark-cli.git mmark-cli
Cloning into 'mmark-cli'...
remote: Counting objects: 63, done.
remote: Compressing objects: 100% (36/36), done.
remote: Total 63 (delta 29), reused 51 (delta 17), pack-reused 0
Unpacking objects: 100% (63/63), done.
$ cd mmark-cli
$ stack build --copy-bins
<SNIP … SNIP>
Copied executables to /home/mark/.local/bin:
- mmark
$ mmark --version
mmark 0.0.1.0 master e60cc92b88e0069ce296d09ef30feecef83fa03e
using mmark     (library) 0.0.5.0
using mmark-ext (library) 0.1.0.0
```

For this you'll need
[Stack](https://docs.haskellstack.org/en/stable/README/), follow the link if
you wish to see the installation instructions.

Next, add the following to your configuration file:

```emacs-lisp
(eval-after-load 'flycheck
  '(add-hook 'flycheck-mode-hook #'flycheck-mmark-setup))
```

Also make sure that you enable the `flycheck-mode` minor mode itself in
`markdown-mode`, this can be done for example like this:

```emacs-lisp
(add-hook 'markdown-mode-hook #'flycheck-mode)
```

## Customization

There is a number of customization options that are available via <kbd>M-x
customize-group flycheck-mmark</kbd>.

## License

Copyright © 2018 Mark Karpov

Distributed under GNU GPL, version 3.
