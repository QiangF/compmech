About
=====

Installation
------------

1) Downloading
..............

The source code repository can be downloaded from
`GitHub <https://github.com/compmech/compmech/archive/master.zip>`_
or cloned using `Git <http://git-scm.com/downloads>`_::

    $ git clone https://github.com/compmech/compmech.git

You can also:

`- Visit the source code page <https://github.com/compmech/compmech>`_

`- Click here to start downloading the latest source code
<https://github.com/compmech/compmech/archive/master.zip>`_

`- Check the released versions
<https://github.com/compmech/compmech/releases>`_



2) Compiling the Cython files
.............................

After you have downloaded the ``compmech-master.zip`` unpack it and go into
the ``compmech-master`` folder. If you cloned using ``git`` go to the
``compmech`` folder.

Run the setup::

   >>> python setup.py

.. Note:: You need Cython and a C compiler for this step.

On Windows 64 bit you should use the free Microsoft SDK compiler,
as explained `in this Cython Github thread <https://github.com/cython/cython/wiki/64BitCythonExtensionsOnWindows>`_.


3) Setting the environment
..........................

Copy the ``compmech`` module (the folder at the same level as the
``README.rst`` file) and paste it to some directory pointed by your
``PYTHONPATH`` environment variable (can be inside the ``site-packages``
directory of your Python installation or any other directory, once you add it
to ``PYTHONPATH``).

3) Testing
..........

TODO, you might be able to use the libraries
`as explained here
<file:///C:/clones/compmech/doc/build/html/modules/index.html>`_.


Requirements
------------
- NumPy
- SciPy
- Cython and a C compiler

Licensing
---------

The new BSD License covers all files in the compmech repository
unless otherwise stated:

.. literalinclude:: ../../LICENSE

