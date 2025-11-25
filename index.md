---
# Copyright © 2025 Marc Nieper-Wißkirchen

# Author: Marc Nieper-Wißkirchen

# Copying and distribution of this file, with or without modification,
# are permitted in any medium without royalty provided the copyright
# notice and this notice are preserved.  This file is offered as-is,
# without any warranty.

layout: default
title: "Egg Scheme"
---

Egg Scheme
==========

![Logo](/assets/logo.png)

Overview
--------

Egg Scheme is a work in progress by its author, Marc
Nieper-Wißkirchen. When the initial programming is done, it will be a
compiler for the [IEEE dialect of the Scheme programming
language](https://standards.ieee.org/ieee/1178/1787/).  Later, Egg
Scheme will support [R6RS Scheme](https://www.r6rs.org).

### Example

```
$ cat examples/fact.ss
(define (fact n)
  (if (zero? n)
      1
      (* n (fact (- n 1)))))
(display (fact 30))
(newline)
$ eggscheme examples/fact.ss
265252859812191058636308480000000
$ eggscheme -ofact examples/fact.ss
$ ./fact
265252859812191058636308480000000
```

Naming
------

In Scheme, procedural macros allow Scheme code to be executed at
compilation time, which results in a chicken-or-egg problem during
bootstrapping a Scheme compiler whose code makes use of procedural
macros.  As there is already an implementation Scheme named
[CHICKEN](https://call-cc.org), the name Egg for the implementation at
hand was born. Despite both names appearing in the same context, Egg
has nothing to do with CHICKEN (and vice versa).

Description
-----------

Egg Scheme compiles a scheme program, given by a set of source files,
to native assembly, which is then assembled and linked to produce a
standalone executable file by the host system's assembler and linker.
The executable dynamically links the Egg Scheme standard library.

Implementation Languages
------------------------

Egg Scheme is implemented in IEEE Scheme with its runtime implemented
in ISO C23.  It can be bootstrapped using an existing IEEE Scheme
implementation, including itself.

Further Developments
--------------------

As soon as the compiler is sufficiently efficient and produces
sufficiently efficient code, the implementation of R6RS will begin.
Once the the R6RS implementation is stable, the implementation will be
extended to support the good parts of R7RS and many SRFIs as well.

License
-------

Egg Scheme is free software licensed under the terms of the GNU Lesser
General Public License.  Programs compiled with Egg Scheme or programs
dynamically linking the Egg Scheme standard library are free to choose
any license whatsoever.

Implementation Details
----------------------

Implementation details that may be of general interest will be
documented here.
