---
title: Subversion migration
layout: wiki
---

This page will outline and detail the information required for
end-users, developers, and undertakers of the task of migrating
Biopython from [CVS](CVS "wikilink") to [Subversion
(SVN)](SVN "wikilink").

Biopython Users
---------------

Content for users to be created.

### Installing Subversion

#### Microsoft Windows

Download and install either
[TortoiseSVN](http://tortoisesvn.tigris.org/) or
[RapidSVN](http://www.rapidsvn.org/). There is also a binary available
for a command line based Subversion client; see the [Subversion
website](http://subversion.tigris.org/project_packages.html#binary-packages).

#### Mac OS X

Download and install Subversion via [Fink](http://fink.sourceforge.net/)
or the [binary
package](http://subversion.tigris.org/project_packages.html#binary-packages).

#### Linux

Some distributions come with the Subversion packages by default, or they
may have already been installed by your system administrator. Verify
whether you have Subversion installed using \`which\` <code>

    user@compy$ which svn
    /usr/bin/svn
    user@compy$ 

</code>

In the above example, Subversion is installed and its executable is
located within `/usr/bin/`.

<code>

    user@compy$ which svn
    user@compy$ 

</code>

On the other hand, in the above example, `which` `svn` returns nothing.
This indicates Subversion is not likely installed. You or your system
administrator will need to use the appropriate package manager to
download and install the packages for Subversion. For example, on
Ubuntu, users would execute the following:

<code>

    user@compy$ sudo apt-get update && sudo apt-get install subversion

</code>

Biopython Developers
--------------------

Existing developer accounts should all continue to work as before. When
working with the main trunk, basic operations such as checking out code,
diff, and committing changes are very similar to those under CVS.

Biopython Migration Strategy
----------------------------

Currently this is being dicussed on the Biopython developers [mailing
list](Mailing_lists "wikilink").
