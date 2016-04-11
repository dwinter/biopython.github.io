---
title: Getting Started
tags:
 - Documentation
 - TODO
---

--[Jblucks](User:Jblucks "wikilink") 16:36, 19 January 2007 (EST): This
page modeled after the one for bioperl

Download
--------

See [Getting BioPython](Download "wikilink")

Installation
------------

See [Installing
BioPython](http://biopython.org/DIST/docs/install/Installation.html)

Quick example
-------------

Executing this:

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

Produces:

    seq is 11 bases long
    reverse complement is CTATCTACATG
    sequence record: Seq('CATGTAGATAG', Alphabet())
    protein translation is HVD
    protein record: Seq('HVD', HasStopCodon(IUPACProtein(), '*'))

Beginners
---------

-   Learn how to program in [Python](http://www.python.org)
    -   [A Byte of
        Python](http://swaroopch.info/text/Byte_of_Python:Main_Page)
    -   [Dive Into Python](http://www.diveintopython.org/toc/index.html)
-   Browse the [Biopython
    Tutorial](http://biopython.org/DIST/docs/tutorial/Tutorial.html)
-   Examine the [Class
    Diagram](http://biopython.org/DIST/docs/api/public/trees.html) if
    you'd like to know more about the relationships between the modules.

Further reading
---------------

-   Read the other [HOWTOs](HOWTOs "wikilink")
-   Use the Wiki Search tools to find more information on
    specific topics.

