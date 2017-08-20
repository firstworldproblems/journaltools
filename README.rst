Overview
========

*journaltools* is a straightforward configuration library for Python.

.. image:: https://travis-ci.org/dhagrow/journaltools.svg?branch=master
    :target: https://travis-ci.org/dhagrow/journaltools



Motivation
----------

Why another configuration library? The simple answer is that none of the
available options give me everything I want, with an API that I enjoy using.
This library provides a lot of powerful functionality, but never at the cost of
simplicity.


Features
--------

* Identification using either title or DOI/ISBN
* Downloading of full journal article with Sci-Hub (https://sci-hub.io)
* Reference file renaming
* Bibtex generation
* Customisaton using configuration file
* Fuzzy search support
* Supports Python 2.7+ and 3.2+.


To do
--------

* Better support for books



Installation
------------

*journaltools* installs using *easy_install* or *pip*::
    
    $ pip install journaltools



Example
-------

Let's download ::
    

```python
j = journaltools()

# download article by title
j.download("Cognitive eipdemiology: Its rise, its current issues, and its challen")

# by DOI
j.download("10.1016/j.paid.2009.11.012")
```

Note that the title provided is both incomplete and contains a typo. The module uses fuzzy string matching, so minor errors are acceptable. 
The article will be downloaded using Sci-Hub. If a captcha is required for downloading, it will load in your gui and you will be asked to solve it before proceeding.


Maybe you're a weirdo like me and are deeply troubled by inconsistent filenames. No problem:

```python

j = journaltools()

# download article by title
journal.rename("Some ambiguously titled reference.pdf")
# by DOI
journal.download("10.1016/j.paid.2009.11.012")
```



First, we specify the defaults and types to expect::
    
    >>> cfg = journaltools.Config('server.cfg')
    >>> cfg.init('server.host', 'localhost')
    >>> cfg.init('server.port', 8080)

Then, we sync our current state with the state of the config file::

    >>> cfg.sync()

As expected, we can access the updated values without undue effort, either
directly::

    >>> cfg['server.host']
    '192.168.1.1'

Or by section. Notice that the type of the *port* option is preserved::
    
    >>> server_cfg = cfg.section('server')
    >>> server_cfg['port']
    9090

Resources
----------

* Documentation_
* PyPI_
* Repository_

.. _Documentation: http://journaltools.rtfd.org/
.. _PyPI: https://pypi.python.org/pypi/journaltools
.. _Repository: https://github.com/firstworldproblems/journaltools
