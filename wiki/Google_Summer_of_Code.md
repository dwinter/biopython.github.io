---
title: Google Summer of Code
---

As part of the Open Bioinformatics Foundation, Biopython is
participating in Google Summer of Code (GSoC) again in 2010. We are
supporting João Rodrigues in his project, "[Extending Bio.PDB:
broadening the usefulness of BioPython's Structural Biology
module](GSOC2010_Joao "wikilink")."

In 2009, Biopython was involved with GSoC in collaboration with our
friends at
[NESCent](https://www.nescent.org/wg_phyloinformatics/Main_Page), and
had two projects funded:

-   Nick Matzke worked on [Biogeographical
    Phylogenetics](https://www.nescent.org/wg_phyloinformatics/Phyloinformatics_Summer_of_Code_2009#Biogeographical_Phylogenetics_for_BioPython).
-   Eric Talevich added support for [parsing and writing
    phyloXML](https://www.nescent.org/wg_phyloinformatics/Phyloinformatics_Summer_of_Code_2009#Biopython_support_for_parsing_and_writing_phyloXML).

Please read the [GSoC page at the Open Bioinformatics
Foundation](http://www.open-bio.org/wiki/Google_Summer_of_Code) and the
main [Google Summer of Code](http://code.google.com/soc) page for more
details about the program. If you are interested in contributing as a
mentor or student next year, please introduce yourself on the [mailing
list](http://biopython.org/wiki/Mailing_lists).

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

:\* Integrate Biopython's [phyloXML
support](http://biopython.org/wiki/Phylo), developed during GSoC 2009,
with PyCogent.

:\* Develop a standardised controller architecture for interrogation of
genome databases by extending PyCogent's Ensembl code, including export
to Biopython objects.

Challenges : This project provides the student with a lot of freedom to create useful interoperability between two feature rich libraries. As opposed to projects which might require churning out more lines of code, the major challenge here will be defining useful APIs and interfaces for existing code. High level inventiveness and coding skill will be required for generating glue code; we feel library integration is an extremely beneficial skill. We also value clear use case based documentation to support the new interfaces.  

<!-- -->

Involved toolkits or projects :  

:\* [Biopython](http://biopython.org/wiki/Main_Page)

:\* [PyCogent](http://pycogent.sourceforge.net/)

Degree of difficulty and needed skills : Medium to Hard. At a minimum, the student will need to be highly competent in Python and become familiar with core objects in PyCogent and Biopython. Sub-projects will require additional expertise, for instance: familiarity with concepts in phylogenetics and genome biology; understanding SQL dialects.  

<!-- -->

Mentors : [Gavin Huttley](http://jcsmr.anu.edu.au/org/dmb/compgen/), [Rob Knight](http://chem.colorado.edu/index.php?option=com_content&view=article&id=263:rob-knight), [Brad Chapman](http://bcbio.wordpress.com), [Eric Talevich](User:EricTalevich "wikilink")  

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

Rationale : The [R statistical language](http://www.r-project.org/) is a powerful open-source environment for statistical computation and visualization. [Python](http://www.python.org/) serves as an excellent complement to R since it has a wide variety of available libraries to make data processing, analysis, and web presentation easier. The two can be smoothly interfaced using [Rpy2](http://bitbucket.org/lgautier/rpy2/), allowing programmers to leverage the best features of each language. Here we propose to build Rpy2 library components to help ease access to phylogenetic and biogeographical libraries in R.  

<!-- -->

Approach : Rpy2 contains higher level interfaces to popular R libraries. For instance, the [ggplot2 interface](http://rpy.sourceforge.net/rpy2/doc-2.1/html/graphics.html#package-ggplot2) allows python users to access powerful plotting functionality in R with an intuitive API. Providing similar high level APIs for biological toolkits available in R would help expose these toolkits to a wider audience of Python programmers. A nice introduction to phylogenetic analysis in R is available from Rich Glor at the [Bodega Bay Marine Lab wiki](http://bodegaphylo.wikispot.org/Phylogenetics_and_Comparative_Methods_in_R). Some examples of R libraries for which integration would be welcomed are:  

:\* [ape (Analysis of Phylogenetics and
Evolution)](http://ape.mpl.ird.fr/) -- an interactive library
environment for phylogenetic and evolutionary analyses

:\* [ade4](http://pbil.univ-lyon1.fr/ADE-4/home.php?lang=eng) -- Data
Analysis functions to analyse Ecological and Environmental data in the
framework of Euclidean Exploratory methods

:\* [geiger](http://cran.r-project.org/web/packages/geiger/index.html)
-- Running macroevolutionary simulation, and estimating parameters
related to diversification from comparative phylogenetic data.

:\* [picante](http://picante.r-forge.r-project.org/) -- R tools for
integrating phylogenies and ecology

:\* [mefa](http://mefa.r-forge.r-project.org/) -- multivariate data
handling for ecological and biogeographical data

Challenges : The student would have the opportunity to learn an available R toolkit, and then code in Python and R to make this available via an intuitive API. This will involve digging into the R code examples to discover the most useful parts for analysis, and then projecting this into a library that is intuitive to Python coders. Beyond the coding and design aspects, the student should feel comfortable writing up use case documentation to support the API and encourage its adoption.  

<!-- -->

Involved toolkits or projects :  

:\* [ape (Analysis of Phylogenetics and
Evolution)](http://ape.mpl.ird.fr/)

:\* [Rpy2](http://bitbucket.org/lgautier/rpy2/)

:\* [Biopython](http://biopython.org/wiki/Main_Page)

Degree of difficulty and needed skills : Moderate. The project requires familiarity with coding in Python and R, and knowledge of phylogeny or biogeography. The student has plenty of flexibility to define the project based on their biological interests (e.g. [microarrays and heatmaps](http://www.warwick.ac.uk/go/peter_cock/python/heatmap/)); there is also the possibility to venture far into data visualization once access to analysis methods is made. [GenGIS](http://kiwi.cs.dal.ca/GenGIS/Main_Page) and can give ideas about what is possible.  

<!-- -->

Mentors : [Laurent Gautier](http://dk.linkedin.com/pub/laurent-gautier/8/81/869), [Brad Chapman](http://bcbio.wordpress.com), [Peter Cock](http://www.scri.ac.uk/staff/petercock)  

### Integration with a third-party structural biology application

Rationale : Biopython is already a useful toolkit for computational structural biology, and Python is a popular language for scripting and configuring a number of separate molecular modelling and simulation tools. Support for controlling these external tools from within Biopython, however, is relatively sparse. This project addresses the issue, starting with a single application.  

<!-- -->

Approach : Select a stable, popular and well-supported third-party application for structural biology (see below) to support from within Biopython. Identify "pain points" that would occur when trying to control various workflows involving your application of choice from Biopython -- e.g. data formats Biopython doesn't yet support, or command-line programs with complex options. In a new Biopython module, write code that makes these common procedures easier to perform, without also making common errors easier to commit.  

<!-- -->

Challenges : Most of the relevant third-party tools have quite extensive functionality, and the corresponding Biopython module should support essentially all of it (unless there's a good reason to skip a particular feature). Some simulation and modelling operations take a long time, too; it should be possible to launch these long-running processes and protect them from interruption.  

<!-- -->

Involved toolkits or projects :  

:\* Biopython: Bio.PDB, and other modules as needed

:\* An external application of your choice: Modeller, AutoDock, PyMol,
MolProbity, ...

Degree of difficulty and needed skills : Medium to hard. Simpler tasks include providing "glue" at each point of I/O; more challenging design problems could come from automating common parts of a simulation or modeling pipeline. Experience in with the tool being wrapped is probably essential.  

<!-- -->

Mentors : [Eric Talevich](User:EricTalevich "wikilink") (looking for co-mentors)  


