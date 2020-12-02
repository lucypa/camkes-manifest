<!--
     Copyright 2018, Data61, CSIRO

     SPDX-License-Identifier: CC-BY-SA-4.0
-->

camkes-manifest
===============
CAmkES is a component platform that provides support for developing and building static
seL4 systems as a collection of interacting components.  The resulting systems are static,
meaning that all the components and their connections (and thus all the kernel
managed resources) are defined at design time and instantiated at system initialisation time.
It is not possible to change the system (e.g., to create or destroy components or to change
the connections between components) at runtime.  This CAmkES package includes various example
systems that can be studied, and individually built and run.

For general instructions on how to use this repository, see [sel4.systems](https://docs.sel4.systems/RepoCheatsheet).

For general information about CAmkES see [the CAmkES pages on seL4.systems](https://docs.sel4.systems/projects/camkes/).

For detailed information about CAmkES see documentation in [the camkes-tool repo](https://github.com/seL4/camkes-tool/blob/master/docs/index.md).

Prerequisites, in addition to a standard build system for your target, are:
* The Haskell compiler, ghc
* Haskell libraries missingH, split and data-ordlist
* Python
* Python libraries python-tempita, pyelftools, jinja2 and ply
* which, realpath and the libxml2 utilities.

## Dependencies for verification

The toolchain can generate formal specifications and proofs about how
a CAmkES spec is mapped to seL4 objects (via capDL). To run these
proofs, checkout the `l4v-master` manifest, e.g. with:

    repo init -m l4v-master.xml
    repo sync

Then enable these extra `init-build` options:

    ../init-build.sh [...] -DCAmkESCapDLStaticAlloc=1 -DCAmkESCapDLVerification=1

You will also need to install additional dependencies; see the
[L4.verified setup instructions](https://github.com/seL4/l4v/blob/master/README.md).

Note that the proof toolchain does not support all CAmkES features.
