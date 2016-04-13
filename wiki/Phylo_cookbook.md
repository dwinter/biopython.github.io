---
title: Phylo cookbook
layout: wiki
tags:
 - Cookbook
---

Here are some examples of using [Bio.Phylo](Phylo "wikilink") for some
likely tasks. Some of these functions might be added to Biopython in a
later release, but you can use them in your own code with Biopython
1.54.

Consensus methods
-----------------

*TODO:*

-   Majority-rules consensus
-   Adams ([Adams
    1972](http://www.faculty.biol.ttu.edu/Strauss/Phylogenetics/Readings/Adams1972.pdf))
-   Asymmetric median tree ([Phillips and Warnow
    1996](http://www.springerlink.com/content/y1x70058822qg257/))

Comparing trees
---------------

*TODO:*

-   Symmetric difference / partition metric, a.k.a. topological distance
-   Quartets distance
-   Nearest-neighbor interchange
-   Path-length-difference

Rooting methods
---------------

*TODO:*

-   Root at the midpoint between the two most distant nodes (or "center"
    of all tips)
-   Root with the given outgroup (terminal or nonterminal)

Graphics
--------

*TODO:*

-   Party tricks with `draw_graphviz`, covering each keyword argument

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

