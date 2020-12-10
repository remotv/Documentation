============
Contributing
============

Remo.TV is an open source project. That means that the code is available for 
free, and that anybody can contribute to it. We're always happy to have new 
contributors even if it's as simple as fixing a spelling error. 

We also discuss our code often on `Discord <https://discord.gg/q3Uvtn5>`_, so 
come check it out!

Robot Controller 
================

The robot controller code is written in Python. There's legacy support for 
Python 2, but all new code is written for Python 3 as Python 2 is 
`deprecated <https://www.python.org/doc/sunset-python-2/>`_. 

Filing a bug report
-------------------
With a GitHub account, you can `submit a bug report <https://github.com/remotv/controller/issues/new?template=bug_report.md>`_
if you've found something that doesn't behave as it should, or even just a typo! 
We have a template that you can/should follow.

Filing a Feature Suggestion
---------------------------
Think we're missing something, let's talk about it! Official feature suggestions
can also be sent on GitHub `here <https://github.com/remotv/controller/issues/new?template=feature_request.md>`_.

Website Code 
============

The website itself is split into two GitHub repositories; the 
`front end <https://github.com/remotv/remo-web-client>`_ and the 
`back end <https://github.com/remotv/remo-platform-server>`_. Because of this,
it's much easier for us to discuss issue reports and feature requests on
Discord, linked above.


Changing the code yourself
==========================
We welcome anybody who wants to contribute their own code to the controller. 
For safety purposes, we don't allow people to push their code directly to the 
repository. Instead, you can follow these instructions:

#. `Fork <https://docs.github.com/en/github/getting-started-with-github/fork-a-repo>`_
   the repository. That copies our controller into a repository that you can write 
   to. You can `clone <https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository>`_ 
   it to your own computer or edit it straight on GitHub.
#. Make your changes. Don't forget to `commit <https://docs.github.com/en/desktop/contributing-and-collaborating-using-github-desktop/committing-and-reviewing-changes-to-your-project>`_ 
   and `push <https://docs.github.com/en/github/using-git/pushing-commits-to-a-remote-repository>`_ 
   to your forked repo.
#. Make a `pull request <https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request-from-a-fork>`_. 
   We'll discuss it and if we decide that it's something that would be beneficial,
   we'll merge it and your code will be part of everyone's robots!

If you do choose to contribute, we ask that you follow conventional coding
practices regarding variable naming, syntax structure, et. cetera. 

The person who writes the technical documentation wishes to request that any
code you add comes with the relevant in-code documentation 
(`JSDoc <https://jsdoc.app>`_ for JavaScript, 
`Javadoc <https://www.oracle.com/technical-resources/articles/java/javadoc-tool.html>`_ 
for Java/Kotlin, and `docstrings <https://www.python.org/dev/peps/pep-0257/>`_ 
for Python). 