---
title: Active projects
---

This page provides a central location to collect references to active
projects. This is a good place to start if you are interested in
contributing to Biopython and want to find larger projects in progress.
For developers, use this to reference git branches or other projects
which you will be working on for an extended period of time. Please keep
it up to date as projects are finished and integrated into Biopython.

Current projects
----------------

### Population Genetics development

Giovanni and Tiago are working on expanding population genetics code in
Biopython. See the [PopGen development page](PopGen_dev "wikilink") for
more details.

### GFF parser

Brad is working on a Biopython GFF parser. Source code is available from
[git hub](http://github.com/chapmanb/bcbb/tree/master/gff). See blog
posts on the [initial
implementation](http://bcbio.wordpress.com/2009/03/08/initial-gff-parser-for-biopython/)
and [MapReduce parallel
version](http://bcbio.wordpress.com/2009/03/22/mapreduce-implementation-of-gff-parsing-for-biopython/).

Project ideas
-------------

Please add any ideas or proposals for new additions to Biopython. Bugs
and enhancements for current code should be discussed though our
bugzilla interface.

-   Use SQLAlchemy, an object relational mapper, for BioSQL internals.
    This would add an additional external dependency to Biopython, but
    provides ready support for additional databases like SQLite. It also
    would provide a raw object interface to BioSQL databases when the
    SeqRecord-like interface is not sufficient. Brad has some initial
    code for this.

<!-- -->

-   Revamp the GEO SOFT parser, drawing on the ideas used in [Sean
    Davis' GEOquery parser in
    R/Bioconductor](http://www.bioconductor.org/packages/bioc/html/GEOquery.html).
    See also [this page](http://www.warwick.ac.uk/go/peter_cock/r/geo/).

Enhancement list
----------------

Maintaining software involves incremental improvements for new format
changes and removal of bugs. Please see our
[bugzilla](http://bugzilla.open-bio.org/) page for a current list. Post
to the developer mailing list if you are interested in tackling any open
issues.
