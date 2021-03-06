The Tamarin prover repository
=============================

This README describes the organization of the repository of the Tamarin prover
for security protocol verification. Its intended audience are interested
users and future developers of the Tamarin prover. For installation
and usage instructions of the Tamarin prover see:
http://www.infsec.ethz.ch/research/software/tamarin.

Developing
----------

We use Linux and Mac OS X during the development of Tamarin. Windows can be
used for development, but the directory layout simplification introduced via
symbolic links will not work.

As of October 1st, 2012, we started organizing our branches according to
http://nvie.com/posts/a-successful-git-branching-model/.
We moreover use the Haskell coding style from
https://github.com/tibbe/haskell-style-guide/blob/master/haskell-style.md.

The simplest way to start developing is to call `make force-install` in the
root directory of this repository. This installs the repository versions of
the `tamarin-prover` package and its supporting libraries
`tamarin-prover-utils`, `tamarin-prover-term`, and `tamarin-prover-theory`
in the global package database. Once this succeeded, compatible versions of
all libraries required by the `tamarin-prover` are also installed in the
global package database. Thus, you can load the `Main` module of the Tamarin
prover by typing `ghci Main` in the root directory of this repository. Note
that, if GHCi prints

~~~~
*** WARNING: /home/repositories/git/github/meiersi/tamarin-prover/.ghci is writable by someone else, IGNORING!
~~~~

, then you have to `chmod g-w` the directory `.` and the GHCi configuration
file `.ghci`.

Note that we welcome all contributions, e.g., further protocol models. Just
send us a pull request.


Version Numbering Policy
-----------------------

We use version numbers with four components.

 - The first component is the major version number. It indicates complete
   rewrites of the codebase.
 - The second component is the minor version number. We use odd minor version
   numbers to denote development releases intended for early adopters. We use
   even minor version numbers to denote public releases, which are also
   published on [Hackage](http://hackage.haskell.org/package/tamarin-prover).
 - The third component indicates bugfix releases.
 - The fourth component indicates documentation and meta-data changes.

We ensure that the external interface of a version of the Tamarin prover is backwards
compatible with the external interface of all versions that agree on the major
and minor version number.

We announce all releases of the Tamarin prover on:
http://www.infsec.ethz.ch/research/software/tamarin.


Manual
------

The manual is `data/doc/MANUAL`. It is part of every installation of the
Tamarin prover.


Example Protocol Models
-----------------------

All example protocol models are found in the directory

    ./data/examples/

, which is also symlinked as `./examples`. All models that we consider stable
are part of every installation of the Tamarin prover. See
`tamarin-prover.cabal` for the list of installed protocols. We use the
following sub-directories to organize the models.

~~~~
csf12/         the AKE case studies from our CSF'12 paper.
classic/       classic security protocols like the ones from
               [SPORE](http://www.lsv.ens-cachan.fr/Software/spore/table.html)
loops/         experiments for testing loop-invariants and protocols with
               non-monotonic state
related_work/  examples from related work on protocols with loops or
               non-monotonic state
experiments/   all other experiments
ake/           more AKE examples including ID-based and tripartite group KE
               protocols based on bilinear pairing
features/      (small) models that demonstrate a given feature
~~~~

Feel free to add more sub-directories and describe them here.

In general, we try use descriptive names for files containing the models. We
also document all our findings as comments in the protocol model.  Moreover,
we use the following header in all files to make their context more explicit.

~~~~
/*
   Protocol:    Example
   Modeler:     Simon Meier, Benedikt Schmidt
   Date:        January 2012

   Status:      working

   Description of protocol.

*/
~~~~
