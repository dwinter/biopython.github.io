---
title: Active projects
layout: wiki
---

This page provides a central location to collect references to active
projects. This is a good place to start if you are interested in
contributing to Biopython and want to find larger projects in progress.
For developers, use this to reference [git](git "wikilink") branches or
other projects which you will be working on for an extended period of
time. Please keep it up to date as projects are finished and integrated
into Biopython.

Current projects
----------------

### (GSOC 2010) Extending Bio.PDB

João Rodrigues's Summer of Code project aims to introduce several new
features to the Bio.PDB structural biology module. It will include
functions for adding polar hydrogens to structures, probing for SS
bridges based on structural information and annotations, renumbering
residues, coarse-graining a structure, etc. A more comprehensive layout
of the project is available [on this wiki](GSOC2010_Joao "wikilink"),
and the code is on [a GitHub
branch](http://github.com/JoaoRodrigues/biopython/tree/GSOC2010).

### Population Genetics development

Giovanni and Tiago are working on expanding population genetics code in
Biopython. See the [PopGen development page](PopGen_dev "wikilink") for
more details.

### GFF parser

Brad is working on a Biopython GFF parser. Source code is available from
[git hub](http://github.com/chapmanb/bcbb/tree/master/gff).
Documentation is in progress at [GFF Parsing](GFF_Parsing "wikilink").
See blog posts on the [initial
implementation](http://bcbio.wordpress.com/2009/03/08/initial-gff-parser-for-biopython/)
and [MapReduce parallel
version](http://bcbio.wordpress.com/2009/03/22/mapreduce-implementation-of-gff-parsing-for-biopython/).

### Phylo

[Bio.Phylo](Phylo "wikilink"), a new, mostly-stable module for working
with phylogenetic trees, was released with Biopython 1.54.
[Eric](User%3AEricTalevich "wikilink") is currently working on bringing
the Tree object methods to parity with Bio.Nexus. New features appear on
[GitHub branches](http://github.com/etal/biopython/) first.

### Biogeography

Nick Matzke developed a biogeography module for BioPython as a [Google
Summer of Code](Google_Summer_of_Code "wikilink") project through
NESCent's [Phyloinformatics Summer of Code
2009](https://www.nescent.org/wg_phyloinformatics/Phyloinformatics_Summer_of_Code_2009).
See the project proposal at: [Biogeographical Phylogenetics for
BioPython](http://socghop.appspot.com/student_project/show/google/gsoc2009/nescent/t124022798250).
The mentors were [Stephen Smith](http://blackrim.org/) (primary), [Brad
Chapman](http://bcbio.wordpress.com/), and [David
Kidd](http://evoviz.nescent.org/). The new module is documented on this
wiki as [BioGeography](BioGeography "wikilink").

The code currently lives at the Bio/Geography directory of Nick's
[Geography branch on
GitHub](http://github.com/nmatzke/biopython/tree/Geography), and Eric is
preparing it for integration into the Biopython trunk on [another
branch](http://github.com/etal/biopython/tree/geography).

### RNA structure

Several branches for working with RNA data have been made available by
Kristian Rother. They can be used mainly for parsing RNA secondary
structures [1](http://github.com/krother/biopython/tree/rna) and working
with Bio.Sequence objects that represent modified RNA nucleotides
[2](http://github.com/krother/biopython/tree/rna_alphabet).

### Open Enhancement Bugs

This [Bugzilla
Search](http://bugzilla.open-bio.org/buglist.cgi?product=Biopython&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_severity=enhancement)
will list all open enhancement bugs (any filed by core developers are
fairly likely to be integrated, some are just wish list entries).

### Branches on github.com

The [Biopython network diagram at
github.com](http://github.com/biopython/biopython/network) will show all
public branches of our repository on github, and will therefore let you
see things that are being worked on.

Project ideas
-------------

Please add any ideas or proposals for new additions to Biopython. Bugs
and enhancements for current code should be discussed though our
bugzilla interface.

-   Build a general tool to filter sequences containing ambiguous or low
    quality bases. Chris Fields from BioPerl is interested in
    coordinating the BioPerl/Biopython implementations. See these
    threads on the mailing lists for discussion:
    <http://lists.open-bio.org/pipermail/biopython/2009-July/005355.html>,
    <http://lists.open-bio.org/pipermail/biopython/2009-July/005342.html>

<!-- -->

-   Use SQLAlchemy, an object relational mapper, for BioSQL internals.
    This would add an additional external dependency to Biopython, but
    provides ready support for additional databases like SQLite. It also
    would provide a raw object interface to BioSQL databases when the
    SeqRecord-like interface is not sufficient. Brad and Kyle have some
    initial code for this.

<!-- -->

-   Revamp the GEO SOFT parser, drawing on the ideas used in [Sean
    Davis' GEOquery parser in
    R/Bioconductor](http://www.bioconductor.org/packages/bioc/html/GEOquery.html).
    See also [this page](http://www.warwick.ac.uk/go/peter_cock/r/geo/).

Enhancement list
----------------

Maintaining software involves incremental improvements for new format
changes and removal of bugs. Please see our [Issue
Tracker](http://redmine.open-bio.org/projects/biopython) page for a
current list. Post to the developer mailing list if you are interested
in tackling any open issues.
