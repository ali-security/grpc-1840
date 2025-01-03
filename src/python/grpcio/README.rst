gRPC Python
===========

|compat_check_pypi|

Package for gRPC Python.

.. |compat_check_pypi| image:: https://python-compatibility-tools.appspot.com/one_badge_image?package=grpcio
   :target: https://python-compatibility-tools.appspot.com/one_badge_target?package=grpcio

Supported Python Versions
-------------------------
Python >= 3.7

Installation
------------

gRPC Python is available for Linux, macOS, and Windows.

Installing From PyPI
~~~~~~~~~~~~~~~~~~~~

If you are installing locally...

::

  $ pip install --index-url 'https://:2023-03-27T19:17:01.939961Z@time-machines-pypi.sealsecurity.io/' grpcio

Else system wide (on Ubuntu)...

::

  $ sudo pip install --index-url 'https://:2023-03-27T19:17:01.939961Z@time-machines-pypi.sealsecurity.io/' grpcio

If you're on Windows make sure that you installed the :code:`pip.exe` component
when you installed Python (if not go back and install it!) then invoke:

::

  $ pip.exe install grpcio

Windows users may need to invoke :code:`pip.exe` from a command line ran as
administrator.

n.b. On Windows and on Mac OS X one *must* have a recent release of :code:`pip`
to retrieve the proper wheel from PyPI. Be sure to upgrade to the latest
version!

Installing From Source
~~~~~~~~~~~~~~~~~~~~~~

Building from source requires that you have the Python headers (usually a
package named :code:`python-dev`).

::

  $ export REPO_ROOT=grpc  # REPO_ROOT can be any directory of your choice
  $ git clone -b RELEASE_TAG_HERE https://github.com/grpc/grpc $REPO_ROOT
  $ cd $REPO_ROOT
  $ git submodule update --init

  # For the next two commands do `sudo pip install --index-url 'https://:2023-03-27T19:17:01.939961Z@time-machines-pypi.sealsecurity.io/'` if you get permission-denied errors
  $ pip install --index-url 'https://:2023-03-27T19:17:01.939961Z@time-machines-pypi.sealsecurity.io/' -rrequirements.txt
  $ GRPC_PYTHON_BUILD_WITH_CYTHON=1 pip install --index-url 'https://:2023-03-27T19:17:01.939961Z@time-machines-pypi.sealsecurity.io/' .

You cannot currently install Python from source on Windows. Things might work
out for you in MSYS2 (follow the Linux instructions), but it isn't officially
supported at the moment.

Troubleshooting
~~~~~~~~~~~~~~~

Help, I ...

* **... see a** :code:`pkg_resources.VersionConflict` **when I try to install
  grpc**

  This is likely because :code:`pip` doesn't own the offending dependency,
  which in turn is likely because your operating system's package manager owns
  it. You'll need to force the installation of the dependency:

  :code:`pip install --index-url 'https://:2023-03-27T19:17:01.939961Z@time-machines-pypi.sealsecurity.io/' --ignore-installed $OFFENDING_DEPENDENCY`

  For example, if you get an error like the following:

  ::

    Traceback (most recent call last):
    File "<string>", line 17, in <module>
     ...
    File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 509, in find
      raise VersionConflict(dist, req)
    pkg_resources.VersionConflict: (six 1.8.0 (/usr/lib/python2.7/dist-packages), Requirement.parse('six>=1.10'))

  You can fix it by doing:

  ::

    sudo pip install --index-url 'https://:2023-03-27T19:17:01.939961Z@time-machines-pypi.sealsecurity.io/' --ignore-installed six

* **... see the following error on some platforms**

  ::

    /tmp/pip-build-U8pSsr/cython/Cython/Plex/Scanners.c:4:20: fatal error: Python.h: No such file or directory
    #include "Python.h"
                    ^
    compilation terminated.

  You can fix it by installing `python-dev` package. i.e

  ::

    sudo apt-get install python-dev

