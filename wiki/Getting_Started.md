---
title: Getting Started
---

Download and Installation
-------------------------

For Windows we provide click-and-run installers. Most Linux
distributions will include an optional Biopython package (although this
may be out of date). Otherwise you typically download and uncompress the
archive, and install from source. See our [downloads
page](Download "wikilink") for details including the prerequisites.

You can check your installation has worked at the python prompt:

``` python
>>> import Bio
```

If that gives no error, you should be done. If you get something like
"ImportError: No module named Bio" something has gone wrong.

Tutorial
--------

The Biopython Tutorial and Cookbook
([HTML](http://biopython.org/DIST/docs/tutorial/Tutorial.html),
[PDF](http://biopython.org/DIST/docs/tutorial/Tutorial.pdf)) contains
the bulk of our documentation. See
[Documentation](Documentation "wikilink") for more links.

Quick example
-------------

Try executing this in python:

``` python
from Bio.Seq import Seq,translate

#create a sequence object of some DNA
my_seq = Seq('CATGTAGATAG')

#print out some details about it
print 'seq is %i bases long' % len(my_seq)
print 'reverse complement is %s' % my_seq.reverse_complement().tostring()

#or see the whole record
print 'sequence record:', my_seq

#translate the sequence into a protein
my_protein = translate(my_seq)

print 'protein translation is %s' % my_protein.tostring()
print 'protein record:', my_protein
```

You should get the following output:

    seq is 11 bases long
    reverse complement is CTATCTACATG
    sequence record: Seq('CATGTAGATAG', Alphabet())
    protein translation is HVD
    protein record: Seq('HVD', HasStopCodon(IUPACProtein(), '*'))

Reading and writing Sequence Files
----------------------------------

If you are using Biopython 1.43 or later, try out the new
[SeqIO](SeqIO "wikilink") module.

Beginners
---------

-   Learn how to program in [Python](http://www.python.org)
    -   [A Byte of
        Python](http://swaroopch.info/text/Byte_of_Python:Main_Page)
    -   [Dive Into Python](http://www.diveintopython.org/toc/index.html)
    -   [Python Quick
        Reference](http://rgruet.free.fr/PQR25/PQR2.5.html)
-   Browse the [Biopython
    Tutorial](http://biopython.org/DIST/docs/tutorial/Tutorial.html)
-   Examine the [Class Diagram](http://biopython.org/DIST/docs/api) if
    you'd like to know more about the relationships between the modules.

Further reading
---------------

-   Use the Wiki Search tools to find more information on
    specific topics.

