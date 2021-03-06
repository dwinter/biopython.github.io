---
title: Building a release
permalink: wiki/Building_a_release
layout: wiki
---

Build Biopython in 23 easy steps!!

Setup required for a new release manager
----------------------------------------

The instructions below require that you have access to a few servers and
the code repository. When you start, be sure to have access to:

1. Write access to the github biopython repo.

2. biopython.org aka cloudportal.open-bio.org. You need to have write
access to write the API and the source tarballs and Windows installers
(might require 2 different operations) under the DIST folder.

3. Wordpress news.open-bio.org with posting permissions.

4. pypi - associated with Biopython.

5. Writing permissions on the wiki page.

If you don't have any of the above, please ask.

The instructions proper
-----------------------

These instructions are for a Unix machine, with a Windows machine also
needed to test and prepare the Windows installers.

1. make sure I have the latest code

`   drevil:~biopython> git pull origin master`

2. bump version numbers and set the release data:

-   Biopython version - edit Bio/\_\_init\_\_.py
-   Biopython Tutorial - update the date/version line in the
    Doc/Tutorial.tex file
-   Biopython README - fill in the release date
-   Make sure to commit the modified files to github.

3. make sure the README file is still up to date

4. add any important info to NEWS or DEPRECATED - you can get a log of
recent git changes like this (adjust the date accordingly):

`   git log --since="2009/08/30" --reverse --pretty="medium"`  
`   `

5. make sure CONTRIB still current

6. make sure setup.py is still up to date

-   Are there any new modules which should get installed?
-   You don't need to update version in setup.py itself (this is now
    done in Bio/\_\_init\_\_.py as described above)

7. do last check to make sure things are checked in

`   > rm -r build`  
`   > rm Tests/*.pyc`  
`   > make clean -C Doc`  
`   > git status`

8. build Biopython and do last regression test

`   drevil:~biopython> python setup.py build `  
`   drevil:~biopython> python setup.py test`

Ideally do this with a clean checkout on your Windows machine too.
Assuming you have setup your compilers etc appropriately just do this:

`   C:\python26\python setup.py build`  
`   C:\python26\python setup.py test`

`   C:\python27\python setup.py build`  
`   C:\python27\python setup.py test`

`   C:\python33\python setup.py build`  
`   C:\python33\python setup.py test`

`   C:\python34\python setup.py build`  
`   C:\python34\python setup.py test`

If you are using MinGW, do not forget to add --compiler=mingw32 (or make
it the default on distutils, see the step on building on windows
machines). Also If you are using a modern MinGW compiler, then distutils
of Python will use an option (-mno-cywgin) that is deprecated and will
break gcc. A possible solution is to [edit
distutils](http://bugs.python.org/issue12641), but on recent Python (3.3
as tested) this seems to have been addressed.

Running the tests simultaneously is risky, as two threads may both try
and read/write to the same temp files.

9. check out clean version somewhere else

`   drevil:~tmp1/> git clone `[`git://github.com/biopython/biopython.git`](git://github.com/biopython/biopython.git)  
`   drevil:~tmp1/> cd biopython`

10. make documentation PDF, text and HTML files in Doc

`   drevil:~biopython> cd Doc`  
`   drevil:~biopython/Doc> make`  
`   drevil:~biopython/Doc> make clean`  
`   drevil:~biopython/Doc> cd ..`

11. make MANIFEST. First, make sure MANIFEST.in up to date.

`   > python setup.py sdist --manifest-only `

12. make the source distribution

`   drevil:~tmp1/biopython> python setup.py sdist --formats=gztar,zip `

13. untar the file somewhere else

`   drevil:~tmp2> tar -xzvf ../tmp1/biopython/dist/biopython-1.53.tar.gz`

-   Check to make sure it includes the HTML and PDF files under Doc

14. make sure I can build and test it

`   drevil:~tmp2/biopython-1.53/> python setup.py build`  
`   drevil:~tmp2/biopython-1.53/> python setup.py test`  
`   drevil:~tmp2/biopython-1.53/> python setup.py install --root . `

A typical source of failure here (on the tests) is the lack of example
files being added to the source distribution: add them to MANIFEST.in

15. Update API documentation using Epydoc (this can often report
otherwise overlooked errors).

-   Go to the ./lib/python2.6/site-packages directory. This is the
    directory created under your source installation after the install
    step above (the name might vary a bit - it should be the place where
    the source packages were "installed"). Running epydoc in your git
    tree works, but can miss some packages due to import errors.

`   epydoc -v -o ~/api -u `[`http://biopython.org`](http://biopython.org)` -n Biopython --docformat plaintext Bio BioSQL`  
`   zip api.zip -r ~/api/`  
`   scp api.zip biopython.org:.`

-   Move the generated ~/api directory to replace
    /home/websites/biopython.org/html/static/DIST/docs/api/ on
    biopython.org (aka cloudportal.open-bio.org).
-   Also update
    /home/websites/biopython.org/html/static/DIST/docs/tutorial with the
    tutorial files

16. add git tag

`   drevil:~biopython> git tag biopython-159`  
`   drevil:~biopython> git push origin master --tags`

17. On your windows machine, build the Windows installers (either from a
clean checkout, or an unzipped copy of the source code bundle made
earlier). Build the installers first, if you do a build/test/install
before hand you seem to get a bloated setup exe. Assuming you have setup
your compilers etc appropriately just do this:

`   C:\python26\python setup.py bdist_wininst`  
`   C:\python27\python setup.py bdist_wininst`  
`   C:\python33\python setup.py bdist_wininst`  
`   C:\python34\python setup.py bdist_wininst`  
`   C:\python35\python setup.py bdist_wininst`  
`   C:\python35\python setup.py bdist_msi`

If you are using MinGW, you will have to make distutils use it (it will
use a MS compiler by default). Here (contrary to the build step) you
cannot pass the compiler as a parameter. The best solution might be to
[configure
distutils](http://stackoverflow.com/questions/3297254/how-to-use-mingws-gcc-compiler-when-installing-python-package-using-pip)

18. Remove any prior Biopython installations on your windows machine,
and confirm the Windows installers work.

19. scp or ftp the .tar.gz, .zip and Windows installer files to the
Biopython website, folder /home/websites/biopython.org/html/static/DIST/
on biopython.org (aka cloudportal.open-bio.org).

20. Upload to the python package index (except for beta/alpha level
releases):

`   > python setup.py register sdist upload`

You need to have a login on pypi and be registered with Biopython to be
able to upload the new version.

21. Update the website and announce the release:

-   before you announce the release, be sure to send your announcement
    text to the biopython-dev mailing list for
    proof-reading/final corrections.
-   add to [main page](Main_Page "wikilink") and [downloads
    page](Download "wikilink") (through the wiki), make sure the links
    work
-   post the announcement on
    [news.open-bio.org](http://news.open-bio.org) (which will update the
    [news page](News "wikilink") and
    [twitter](http://twitter.com/Biopython) via the news feed)
-   add the new version to
    [RedMine](https://redmine.open-bio.org/projects/biopython)
-   send email to biopython@biopython.org and
    biopython-announce@biopython.org (see [mailing
    lists](Mailing_lists "wikilink"))
-   forward the email to Linux packagers e.g.
    debian-med@lists.debian.org

22. Ask Peter, Brad, or Bjoern to prepare a new Galaxy package on
<https://github.com/biopython/galaxy_packages> and upload it to the main
and test Galaxy ToolShed

23. Bump version numbers again

-   Update Bio/\_\_init\_\_.py version
-   Biopython Tutorial - update the date/version line in the
    Doc/Tutorial.tex file
-   Make sure to commit the modified files to github.

Add a plus to the version to note that development is after the said
version. E.g. if you have \_\_version\_\_ = "1.61", make it 1.61+
