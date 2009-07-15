---
title: Remove PDB disordered atoms
layout: wiki
tags:
 - Cookbook
---

Problem
-------

You have a PDB with disordered atoms, i.e. different atomic positions
with occupancies that add up to 100%. From this PDB you want to create a
new one having only one set of the disordered atoms. This can be
necessary if you want to perform RMSD calculations or Molecular Dynamics
simulations.

Solution
--------

[Bio.PDB](http://biopython.org/DIST/docs/tutorial/Tutorial.html#htoc118 "wikilink")
is proficient in dealing disordered atoms. Each disordered atom has a
property indicating its alternative positions: atom.altloc. Usually
there are only two alternative positions labelled 'A' and 'B'