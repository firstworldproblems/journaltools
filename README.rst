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

* Automatic value conversion.
* Section nesting.
* Dict-like access.
* Single-file module with no dependencies.
* Extensible input/output formats.
* Built-in support for INI files and the Windows registry.
* Preserves ordering and comments of INI files.
* Full Unicode support.
* Supports Python 2.7+ and 3.2+.

Installation
------------

*journaltools* installs using *easy_install* or *pip*::
    
    $ pip install journaltools

Example
-------

Basic usage is cake. Let's assume our config file looks like this::
    
    [server]
    host = 192.168.1.1
    port = 9090

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
