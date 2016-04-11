---
title: Google Summer of Code
layout: wiki
---

Biopython was involved with the 2009 Google Summer of Code (GSoC) in
collaboration with our friends at
[NESCent](https://www.nescent.org/wg_phyloinformatics/Main_Page), and
had two projects funded:

-   Nick Matzke worked on [Biogeographical
    Phylogenetics](https://www.nescent.org/wg_phyloinformatics/Phyloinformatics_Summer_of_Code_2009#Biogeographical_Phylogenetics_for_BioPython).
-   Eric Talevich added support for [parsing and writing
    phyloXML](https://www.nescent.org/wg_phyloinformatics/Phyloinformatics_Summer_of_Code_2009#Biopython_support_for_parsing_and_writing_phyloXML).

In 2010 we hope to be continue working with GSoC. If you are interested
in contributing as a mentor or student, please introduce yourself on the
[mailing list](http://biopython.org/wiki/Mailing_lists).

2010 Project ideas
------------------

### Biopython and PyCogent interoperability

Rationale : [PyCogent](http://pycogent.sourceforge.net/) and [Biopython](http://biopython.org/wiki/Main_Page) are two widely used toolkits for performing computational biology and bioinformatics work in Python. The libraries have had traditionally different focuses: with Biopython focusing on sequence parsing and retrieval and PyCogent on evolutionary and phylogenetic processing. Both user communities would benefit from increased interoperability between the code bases, easing the developing of complex workflows.  

<!-- -->

Approach : The student would focus on soliciting use case scenarios from developers and the larger communities associated with both projects, and use these as the basis for adding glue code and documentation to both libraries. Some use cases of immediate interest as a starting point are:  

:\* Allow round-trip conversion between biopython and pycogent core
objects (sequence, alignment, tree, etc.).

:\* Building workflows using Codon Usage analyses in PyCogent with
clustering code in Biopython.

:\* Connecting Biopython acquired sequences to PyCogent's alignment,
phylogenetic tree preparation and tree visualization code.

:\* Integrate Biopython's [PhyloXML
support](http://biopython.org/wiki/Phylo), developed during GSoC 2009,
with PyCogent.

:\* Improve database interoperability by extending pycogent's Ensembl
code to operate on additional genome databases, exporting these to
Biopython objects.

Challenges : This project provides the student with a lot of freedom to create useful interoperability between two feature rich libraries. As opposed to projects which might require churning out more lines of code, the major challenge here will be defining useful APIs and interfaces for existing code. High level inventiveness and coding skill will be required for generating glue code; we feel library integration is an extremely beneficial skill. We also value clear use case based documentation to support the new interfaces.  

<!-- -->

Involved toolkits or projects :  

:\* [Biopython](http://biopython.org/wiki/Main_Page)

:\* [PyCogent](http://pycogent.sourceforge.net/)

Degree of difficulty and needed skills : Medium to Hard. In addition to feeling comfortable working with existing libraries and programming in Python, this will require good communication skills to solicit and integrate feedback from existing Biopython and PyCogent users.  

<!-- -->

Mentors : [Gavin Huttley](http://jcsmr.anu.edu.au/org/dmb/compgen/), [Rob Knight](http://chem.colorado.edu/index.php?option=com_content&view=article&id=263:rob-knight),[Brad Chapman](http://bcbio.wordpress.com)  

### Galaxy phylogenetics pipeline development

Rationale : [Galaxy](http://main.g2.bx.psu.edu/) is a popular web based interface for integrating biological tools and analysis pipelines. It is widely used by bench biologists for their analysis work, and by computational biologists for building interfaces to developed tools. [HyPhy](http://hyphy.org) provides a popular package for molecular evolution and sequence statistical analysis, and the [datamonkey.org](http://www.datamonkey.org/) server provides web based workflows to perform a number of common tasks with HyPhy. This project bridges these two complementary projects by bringing HyPhy workflows into the Galaxy system, standardizing these analyses on a widely used platform.  

<!-- -->

Approach : The student would bring existing workflows from datamonkey.org to Galaxy. The general approach would be to pick a datamonkey.org workflow, wrap the relevant tools using [Galaxy's XML tool definition language](http://bitbucket.org/galaxy/galaxy-central/wiki/AddToolTutorial), and implement a shared pipeline with [Galaxy's workflow system](http://screencast.g2.bx.psu.edu/galaxy/flash/WorkflowFromHistory.html). Functional tests will be developed for tools and workflows, along with high level documentation for end users.  

<!-- -->

Challenges : This project requires the student to become comfortable working in the existing Galaxy framework. This is a useful practical skill as Galaxy is widely used in the biological community. Similarly, the student should become familiar with the statistical evolutionary methods in HyPhy to feel comfortable wrapping and testing them in Galaxy. Since the tools would be widely used from the main Galaxy website and installed instances, we place a strong emphasis on students who feel comfortable building tests and examples that would ensure the developed workflows function as expected.  

<!-- -->

Involved toolkits or projects :  

:\* [Galaxy](http://bitbucket.org/galaxy/galaxy-central/wiki/Home)

:\* [HyPhy](http://hyphy.org)

:\* [Adaptive Evolution Server](http://www.datamonkey.org)

Degree of difficulty and needed skills : Medium to Hard. As envisioned, the project would involve implementing full phylogenetic pipelines with the Galaxy toolkits. This would require becoming familiar with the Galaxy tool integration framework as well as being comfortable with HyPhy tools and current pipelines. This would involve comfort with XML for developing the tool interfaces, and Python for integrating scripts and tests with Galaxy and HyPhy.  

<!-- -->

Mentors : [Sergei L Kosakovsky Pond](http://www.hyphy.org/sergei/), [Brad Chapman](http://bcbio.wordpress.com), [Anton Nekrutenko](http://www.bx.psu.edu/~anton/)  

### Accessing R phylogenetic tools from Python

Rationale :  

<!-- -->

Approach :  

<!-- -->

Challenges :  

<!-- -->

Involved toolkits or projects :  

<!-- -->

Degree of difficulty and needed skills :  

<!-- -->

Mentors : [Laurent Gautier](http://dk.linkedin.com/pub/laurent-gautier/8/81/869), [Brad Chapman](http://bcbio.wordpress.com)  


