==========
Installing
==========

.. note::

    If you wish to contribute to the project, it's recommended you
    :ref:`install the latest development version<install_from_source>`.

.. contents::

Installing an official release
==============================

Matplotlib and its dependencies are available as wheel packages for macOS,
Windows and Linux distributions::

  python -m pip install -U pip
  python -m pip install -U matplotlib

.. note::

   The following backends work out of the box: Agg, ps, pdf, svg and TkAgg.

   For support of other GUI frameworks, LaTeX rendering, saving
   animations and a larger selection of file formats, you may need to
   install :ref:`additional dependencies <install_requirements>`.

Although not required, we suggest also installing ``IPython`` for
interactive use.  To easily install a complete Scientific Python
stack, see :ref:`install_scipy_dists` below.

Test data
---------

The wheels (:file:`*.whl`) on the `PyPI download page
<https://pypi.org/project/matplotlib/>`_ do not contain test data
or example code.

If you want to try the many demos that come in the Matplotlib source
distribution, download the :file:`*.tar.gz` file and look in the
:file:`examples` subdirectory.

To run the test suite:

* extract the :file:`lib/matplotlib/tests` or :file:`lib/mpl_toolkits/tests`
  directories from the source distribution;
* install test dependencies: `pytest <https://pypi.org/project/pytest>`_,
  Pillow, MiKTeX, GhostScript, ffmpeg, avconv, ImageMagick, and `Inkscape
  <https://inkscape.org/>`_;
* run ``python -mpytest``.

Third-party distributions of Matplotlib
=======================================

.. _install_scipy_dists:

Scientific Python Distributions
-------------------------------

`Anaconda <https://www.anaconda.com/>`_ and `Canopy
<https://www.enthought.com/products/canopy/>`_ and `ActiveState
<https://www.activestate.com/activepython/downloads>`_ are excellent
choices that "just work" out of the box for Windows, macOS and common
Linux platforms. `WinPython <https://winpython.github.io/>`_ is an
option for Windows users.  All of these distributions include
Matplotlib and *lots* of other useful (data) science tools.

Linux: using your package manager
---------------------------------

If you are on Linux, you might prefer to use your package manager.  Matplotlib
is packaged for almost every major Linux distribution.

* Debian / Ubuntu: ``sudo apt-get install python3-matplotlib``
* Fedora: ``sudo dnf install python3-matplotlib``
* Red Hat: ``sudo yum install python3-matplotlib``
* Arch: ``sudo pacman -S python-matplotlib``

.. _install_from_source:

Installing from source
======================

If you are interested in contributing to Matplotlib development,
running the latest source code, or just like to build everything
yourself, it is not difficult to build Matplotlib from source.  Grab
the latest *tar.gz* release file from `the PyPI files page
<https://pypi.org/project/matplotlib/>`_, or if you want to
develop Matplotlib or just need the latest bugfixed version, grab the
latest git version, and see :ref:`install-from-git`.

The standard environment variables :envvar:`CC`, :envvar:`CXX`,
:envvar:`PKG_CONFIG` are respected.  This means you can set them if your
toolchain is prefixed. This may be used for cross compiling. ::

  export CC=x86_64-pc-linux-gnu-gcc
  export CXX=x86_64-pc-linux-gnu-g++
  export PKG_CONFIG=x86_64-pc-linux-gnu-pkg-config

Once you have satisfied the requirements detailed below (i.e., Python and
FreeType), you can build Matplotlib.
::

  cd matplotlib
  python -m pip install .

We provide a setup.cfg_ file which you can use to customize the build
process. For example, which default backend to use, whether some of the
optional libraries that Matplotlib ships with are installed, and so on.  This
file will be particularly useful to those packaging Matplotlib.

.. _setup.cfg: https://raw.githubusercontent.com/matplotlib/matplotlib/master/setup.cfg.template

.. _install_requirements:

Dependencies
------------

Matplotlib requires the following dependencies:

* `Python <https://www.python.org/downloads/>`_ (>= 3.6)
* `FreeType <https://www.freetype.org/>`_ (>= 2.3)
* `NumPy <http://www.numpy.org>`_ (>= 1.11)
* `setuptools <https://setuptools.readthedocs.io/en/latest/>`_
* `cycler <http://matplotlib.org/cycler/>`_ (>= 0.10.0)
* `dateutil <https://pypi.org/project/python-dateutil>`_ (>= 2.1)
* `kiwisolver <https://github.com/nucleic/kiwi>`_ (>= 1.0.0)
* `pyparsing <https://pyparsing.wikispaces.com/>`_

Optionally, you can also install a number of packages to enable better user
interface toolkits. See :ref:`what-is-a-backend` for more details on the
optional Matplotlib backends and the capabilities they provide.

* `Tk <https://docs.python.org/3/library/tk.html>`_ (>= 8.3, != 8.6.0 or
  8.6.1): for the Tk-based backends;
* `PyQt4 <https://pypi.org/project/PyQt4>`_ (>= 4.6) or
  `PySide <https://pypi.org/project/PySide>`_ (>= 1.0.3) [#]_: for the
  Qt4-based backends;
* `PyQt5 <https://pypi.org/project/PyQt5>`_: for the Qt5-based backends;
* `PyGObject <https://pypi.org/project/PyGObject/>`_: for the GTK3-based
  backends [#]_;
* `wxPython <https://www.wxpython.org/>`_ (>= 4) [#]_: for the wx-based
  backends;
* `cairocffi <https://cairocffi.readthedocs.io/en/latest/>`_ (>= 0.8) or
  `pycairo <https://pypi.org/project/pycairo>`_: for the cairo-based
  backends;
* `Tornado <https://pypi.org/project/tornado>`_: for the WebAgg backend;

.. [#] PySide cannot be pip-installed on Linux (but can be conda-installed).
.. [#] If using pip (and not conda), PyGObject must be built from source; see
       https://pygobject.readthedocs.io/en/latest/devguide/dev_environ.html.
.. [#] If using pip (and not conda) on Linux, wxPython wheels must be manually
       downloaded from https://wxpython.org/pages/downloads/.

For better support of animation output format and image file formats, LaTeX,
etc., you can install the following:

* `ffmpeg <https://www.ffmpeg.org/>`_/`avconv
  <https://libav.org/avconv.html>`_: for saving movies;
* `ImageMagick <https://www.imagemagick.org/script/index.php>`_: for saving
  animated gifs;
* `Pillow <https://pillow.readthedocs.io/en/latest/>`_ (>= 3.4): for a larger
  selection of image file formats: JPEG, BMP, and TIFF image files;
* `LaTeX <https://miktex.org/>`_ and `GhostScript (>=9.0)
  <https://ghostscript.com/download/>`_ : for rendering text with LaTeX.

FreeType
--------

Matplotlib depends on FreeType, a font rendering library.  It can either
download and build its own copy of the library, or use a copy of FreeType
already installed in your system.

The easiest option is to make Matplotlib download and build FreeType.  This is
done by setting the :envvar:`MPLLOCALFREETYPE` environment variable to 1 -- on
Linux and OSX:

.. code-block:: sh

   export MPLLOCALFREETYPE=1

and on Windows:

.. code-block:: bat

   set MPLLOCALFREETYPE=1

and you can continue the installation (``python -m pip install .``), ignoring
everything that follows.

If you wish, instead, to use the system FreeType, you need to install the
FreeType library and headers.  This can be achieved using a package manager:

.. code-block:: sh

   # Pick ONE of the following:
   sudo apt install libfreetype6-dev  # Debian/Ubuntu
   sudo dnf install freetype-devel  # Fedora
   brew install freetype  # macOS with Homebrew
   conda install freetype  # conda, any OS

On Linux and macOS, it is also recommended to install pkg-config_, a helper
tool for locating FreeType:

.. code-block:: sh

   # Pick ONE of the following:
   sudo apt install pkg-config  # Debian/Ubuntu
   sudo dnf install pkgconf  # Fedora
   brew install pkg-config  # macOS with Homebrew
   conda install pkg-config  # conda

.. _pkg-config: https://www.freedesktop.org/wiki/Software/pkg-config/

If not using pkg-config (in particular on Windows), you may need to set the
include path (to the FreeType headers) and link path (to the FreeType library)
explicitly, if they are not in standard locations.  This can be done using
standard environment variables -- on Linux and OSX:

.. code-block:: sh

   export CFLAGS='-I/directory/containing/ft2build.h'
   export LDFLAGS='-L/directory/containing/libfreetype.so'

and on Windows:

.. code-block:: bat

   set CL=/IC:\directory\containing\ft2build.h
   set LINK=/LIBPATH:C:\directory\containing\freetype.lib

.. note::

  The following libraries are shipped with Matplotlib:

  - ``Agg``: the Anti-Grain Geometry C++ rendering engine;
  - ``qhull``: to compute Delaunay triangulation;
  - ``ttconv``: a TrueType font utility.

.. _build_windows:

Building on Windows
-------------------

The Python shipped from https://www.python.org is compiled with Visual Studio
2015 for 3.5+.  Python extensions should be compiled with the same
compiler, see e.g.
https://packaging.python.org/guides/packaging-binary-extensions/#binary-extensions-for-windows
for how to set up a build environment.

If you are building your own Matplotlib wheels (or sdists), note that any DLLs
that you copy into the source tree will be packaged too.

Conda packages
--------------

The conda packaging scripts for Matplotlib are available at
https://github.com/conda-forge/matplotlib-feedstock.
