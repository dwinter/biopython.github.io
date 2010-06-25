---
title: Phylo cookbook
layout: wiki
---

Here are some examples of using Bio.Phylo for some likely tasks. Some of
the given functions might be added to Biopython in a later release, but
you can use them in your own code with Biopython 1.54.

Consensus methods
-----------------

*TODO:*

-   Majority-rules consensus

Rooting methods
---------------

*TODO:*

-   Root at the midpoint between the two most distant nodes (or "center"
    of all tips)
-   Root with the given outgroup (terminal or nonterminal)

Exporting to other types
------------------------

### Convert to a PyCogent tree

The tree objects used by Biopython and PyCogent are different.
Nonetheless, both toolkits support the Newick file format, so
interoperability is straightforward at that level:

``` python
from Bio import Phylo
import cogent

Phylo.write(bptree, 'mytree.nwk', 'newick')  # Biopython tree
ctree = cogent.LoadTree('mytree.nwk')        # PyCogent tree
```

*TODO:*

-   Convert objects directly, preserving some PhyloXML annotations if
    possible

### Convert to a NumPy array or matrix

*TODO:*

-   Adjacency matrix: cells are True if parent-child relationship
    exists, otherwise False
-   Distance matrix: cells are branch lengths if a branch exists,
    otherwise Inf or NaN
-   Relationship matrix? See [Martins and Housworth
    2002](http://www.jstor.org/stable/3070822)
