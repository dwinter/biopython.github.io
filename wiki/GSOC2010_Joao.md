---
title: GSOC2010 Joao
layout: wiki
---

Author & Mentors
----------------

[João Rodrigues](User%3AJoaor "wikilink") anaryin@gmail.com

**Mentors**

  
Eric Talevich

Diana Jaunzeikare

Peter Cock

Abstract
--------

Biopython is a very popular library in Bioinformatics and Computational
Biology. Its Bio.PDB module, originally developed by Thomas Hamelryck,
is a simple yet powerful tool for structural biologists. Although it
provides a reliable PDB parser feature and it allows several
calculations (Neighbour Search, RMS) to be made on macromolecules, it
still lacks a number of features that are part of a researcher's daily
routine. Probing for disulphide bridges in a structure and adding polar
hydrogen atoms accordingly are two examples that can be incorporated in
Bio.PDB, given the module's clever structure and good overall
organisation. Cosmetic operations such as chain removal and residue
renaming – to account for the different existing nomenclatures – and
renumbering would also be greatly appreciated by the community.

Another aspect that can be improved for Bio.PDB is a smooth
integration/interaction layer for heavy-weights in macromolecule
simulation such as MODELLER, GROMACS, AutoDock, HADDOCK. It could be
argued that the easiest solution would be to code hooks to these
packages' functions and routines. However, projects such as the recently
developed
[edPDB](http://sbcb.bioch.ox.ac.uk/oliver/software/GromacsWrapper/html/edpdb.html)
or the more complete [Biskit library](http://biskit.pasteur.fr/) render,
in my opinion, such interfacing efforts redundant. Instead, I believe it
to be more advantageous to include these software' input/output formats
in Biopython's SeqIO and AlignIO modules. This, together with the
creation of interfaces for model validation/structure checking
services/software would allow Biopython to be used as a pre- and
post-simulation tool. Eventually, it would pave the way for its
inclusion in pipelines and workflows for structure modelling, molecular
dynamics, and docking simulations.

Project Schedule
----------------

The schedule below was organised to be flexible, which means that some
features will likely be done early. Also, the weeks include
documentation and unit testing efforts for the features, with extended
periods for reviewing these efforts at the two points during the project
(halfway, final week).

### Community Bonding Period

-   Getting familiar with development environment (Git Hub account, Git,
    Biopython's repository, Bug tracking system, etc)

<!-- -->

-   Gather scientific literature and discuss some of the
    to-be-implemented methods.

### Week 1 \[31st May - 6th June\]

#### Renumbering residues of a structure

-   Read SEQRES record to account for gaps
-   Alternatively read ATOM records.

#### Probe disulphide bridges in the structure

-   Via NeighbourSearch class
-   Also use SSBOND in header

#### Extract Biological Unit

-   REMARK350 contains rotation and translation information
-   If REMARK is absent, do nothing.

### Week 2 \[7th – 13th June\]

#### Structure Hydrogenation

-   Add all/polar hydrogens through interface with WHATIF server.
-   Optionally define a set pH
    -   [pKa values
        algorithm](http://www3.interscience.wiley.com/journal/112117957/abstract)

#### Hydrogenation Report

-   Produces a brief list of polar hydrogen atoms in the structure.
    -   Chain | Residue \[number\] | Atom

### Weeks 3-5 \[14th June- 4th July\]

#### Removal of disordered atoms

-   [Solution proposed in the Biopython
    wiki](Remove_PDB_disordered_atoms "wikilink")

#### Residue name normalisation

-   Build conversion table from different nomenclatures (research them
    during c.bonding period )
-   Write function to make a given structure compliant with a given
    software nomenclature:
    -   Amber
    -   CNS/HADDOCK
    -   GROMACS

#### Coarse Grain Structure

-   Implement function to reduce complexity of a structure
    -   1pt\*c-alpha
    -   2pt\*c-alpha / c-beta
    -   3pt\*c-alpha / c-beta / side-chain pseudo-centroid OR side-chain
        centroid

### Week 6 (Mid-Term) \[5th - 11th July\]

  
Testing and consolidating the features thoroughly.

Write documentation & examples for each feature, to be included in
Biopython's Wiki and Bio.PDB's FAQ.

Mid-term Evaluations. Discussing with mentors current state of project
and adjust following schedule to comply with project's needs.

### Week 7 \[12th - 19th July\]

#### Add support for MODELLER's PIR format to Biopython

-   [Format
    Description](http://www.salilab.org/modeller/manual/node445.html#alignmentformat)
-   SeqIO
-   AlignIO

#### Allow conversion of Structure Object to Sequence Object

-   Based on Bio.PDB.Polypeptide function

### Weeks 8-10 \[20th July - 9th August\]

#### Add Sequence/Structure Homology functions

-   Create call to Biopython's BLAST interfaces
    -   Allow direct blast from structure object ( e.g.
        protein.find\_homoseq() )
    -   Returns list of tuples with E-Value \*Dictionary (name, length
        of alignment, etc..)
-   Create interface with structural homology web services
    -   e.g. [Dali
        server](http://ekhidna.biocenter.helsinki.fi/dali_server/)
    -   Return list of tuples with Z-Score\*Dictionary (name, etc...)

#### Implement basic structure validation checks

-   Via NeighbourSearch class
    -   Same Charge contacts
    -   Atom Clashes
-   Via ResidueDepth Class
    -   Buried Charges
-   Interface WHATIF PDBReport web service
    -   Parse WARNING and ERROR messages

### Week 11 \[10th - 17th August\]

#### Reviewing documentation, code, write tests for new functions.

Project Code
------------

Hosted at [this GitHub
branch](http://github.com/JoaoRodrigues/biopython/tree/GSOC2010)

Project Progress
----------------

Since I'm adding some methods that are useful/logical only for proteins,
having them exposed in Structure.py for every molecule could be
misleading. We decided then to add a 'as\_protein()' method that allows
protein-specific methods to be accessed. The following example
demonstrates how this call works. Note how the "search\_ss\_bonds"
method is absent from dir(s) but not from dir(prot).

``` python
from Bio.PDB import PDBParser

p = PDBParser()
s = p.get_structure('example', '4PTI.pdb')

dir(s)
# Cut for viewing purposes
['__doc__', ... , 'renumber_residues', 'set_parent', 'xtra']

prot = s.as_protein()

dir(prot)

['__doc__', ... , 'renumber_residues', 'search_ss_bonds', 'set_parent', 'xtra']
```

### Week 1

#### Renumbering residues of a structure

Since parse\_pdb\_header is far from optimal and is likely to change in
the future, I opted to forfeit reading SEQREQ records to account for
gaps. However, ignoring this information and renumbering based on ATOM
records would make us lose information on gaps. I opted to subtract the
first residue number-1 to all residues thus making the numbering start
in 1 and still keep gaps. I also added an argument (start) to allow the
user to set which number to start the counting from.

Example:

``` python
from Bio.PDB import PDBParser

p = PDBParser()
s = p.get_structure('example', '1IHM.pdb')

print list(s.get_residues())[0]
<Residue ASP het=  resseq=1029 icode= >

s.renumber_residues()
print list(s.get_residues())[0]
<Residue ASP het=  resseq=1 icode= >
```

#### Probe disulphide bridges in the structure

The same rationale from SEQRES applies for the exclusion of looking up
SSBOND. Also, instead of using NeighborSearch to look for pairs of
cysteins in bond distance, I instead used the minus operator since it
has been overloaded to return the distance between two atoms (Page 10 of
the [FAQ](http://www.biopython.org/DIST/docs/cookbook/biopdb_faq.pdf)).
The average distance cited in the literature is 2.05A but other software
packages and my own tests set 3.0A as a good threshold. Still, the user
can set his own threshold manually.

The function returns an iterator with tuples of pairs of residues.

``` python
from Bio.PDB import PDBParser

p = PDBParser()
s = p.get_structure('example', '4PTI.pdb')

prot = s.as_protein()

for bond in prot.search_ss_bonds():
  print bond

(<Residue CYS het=  resseq=5 icode= >, <Residue CYS het=  resseq=55 icode= >)
(<Residue CYS het=  resseq=14 icode= >, <Residue CYS het=  resseq=38 icode= >)
(<Residue CYS het=  resseq=30 icode= >, <Residue CYS het=  resseq=51 icode= >)
```

#### Extract Biological Unit

Added parsing for REMARK350 to parse\_pdb\_header since there was
already a bit written for another REMARK section. This extracts the
transformation matrices and the translation vector from the header, that
is then fed to the Structure function. Each new rotated structure is
created as a new MODEL. I chose this because crystal structures very
rarely have more than one MODEL instance and also because NMR models
don't have REMARK 350 that often (at least to my knowledge).

``` python
from Bio.PDB import PDBParser

p = PDBParser()


s1 = p.get_structure('a', '4PTI.pdb')
s1.build_biological_unit()
'Processed 0 transformations on the structure.' # Identity matrix is ignored.

s2 = p.get_structure('b', 'homol_1bd8.pdb') # A homology model
s2.build_biological_unit()
'PDB File lacks appropriate REMARK 350 entries to build Biological Unit.'

s3 = p.get_structure('c', '1IHM.pdb')
s3.build_biological_unit()
'Processed 59 transformations on the structure.'
```

### Weeks 2 and 3

#### Hydrogenation of PDB files

Following discussion between the mentors and me, we decided that maybe
it was better to not only include a webserver for this purpose but also
a local algorithm. This would not limit the user when there he/she lacks
an internet connection.

Our webserver of choice was WHATIF. The simplicity of its access
justifies its choice, together with the stability and proven results of
the method. The service we want to implement is available as a test
webservice via a REST or SOAP interface. Access is as simple as this,
via REST:

``` python
#!/usr/bin/python

import urllib
import xml.dom.minidom

# read a local PDB file
f = open('../pdb1crn.ent', 'r')
data = f.read()
f.close()

# now upload this PDB file to the What IF webservice
f = urllib.urlopen("http://www.cmbi.ru.nl/wiwsd/rest/UploadPDB", data)
x = xml.dom.minidom.parse(f)
id = x.getElementsByTagName("response")[0].childNodes[0].data

# Call a what-if function, we use SymmetryContact as an example
f = urllib.urlopen("http://www.cmbi.ru.nl/wiwsd/rest/SymmetryContact/id/" + id)
x = xml.dom.minidom.parse(f)

# and now we have the data, print out a simple list
for node in x.getElementsByTagName("response"):
    nr = node.getElementsByTagName("number")[0].childNodes[0].data
    cnt = node.getElementsByTagName("contact_count")[0].childNodes[0].data
    print nr + "\t" + cnt
```

We are still discussing about the technical details of the
implementation.

Regarding the local algorithm, several approaches were studied:
[HAAD](http://zhang.bioinformatics.ku.edu/HAAD/),
[GROMACS](http://manual.gromacs.org/current/online/protonate.html),
PyMol[3](http://pymolwiki.org/index.php/H_Add),
MMTK[4](http://sourcesup.cru.fr/projects/mmtk/). All of them add
hydrogens based on geometrical criteria, with HAAD doing some sort of
pseudo-minimization to get the atoms in the right orientation. Although
I think this is valuable strategy, it is a bit beyond the scope of this
project. Furthermore, the only way I know of getting perfectly good
orientations is under a real force field. Therefore, I believe that
adding hydrogens based on geometrical constraints is a simple yet good
addition to BioPython.

I am still studying the algorithms to try and replicate their efficiency
(don't want to reinvent the wheel). Since some of the code is GPL'ed it
can be directly associated with our library.

#### Coarse Grain Structure

This feature has been written and implemented for proteins only. It was
based on ENCADs coarse graining strategy (3pt per residue) but I'm still
adding CABS structure too. I wrote a center of mass function that is
independent of any Entity subclass and can therefore be useful for other
purposes. We are deciding where to place this code. I will add an
example when the code is mature enough.