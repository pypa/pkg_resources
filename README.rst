.. image:: https://img.shields.io/pypi/v/pkg_resources.svg
   :target: https://pypi.org/project/pkg_resources

.. image:: https://img.shields.io/pypi/pyversions/pkg_resources.svg

.. image:: https://img.shields.io/travis/pypa/pkg_resources/master.svg
   :target: https://travis-ci.org/pypa/pkg_resources

.. .. image:: https://img.shields.io/appveyor/ci/pypa/pkg_resources/master.svg
..    :target: https://ci.appveyor.com/project/pypa/pkg_resources/branch/master

.. .. image:: https://readthedocs.org/projects/pkg_resources/badge/?version=latest
..    :target: https://pkg_resources.readthedocs.io/en/latest/?badge=latest


Testing
=======

It may be tricky to test pkg_resources, as it may easily conflict with an installed one.

There's a working path (assuming you're storing your venvs in ~/.venvs)::

  python3 -m venv ~/.venvs/pkg_resources
  pip install six appdirs packaging  # A python3 -m pip install -e .[testing] won't work
                                     # at this point, as it will try to use the
                                     # pkg_resources from the current directory,
                                     # needing six, but not yet having it
  pip install -e .[testing]  # This one should pass, using the ./pkg_resources.
  pytest  # This one should pass too, and should test ./pkg_resources
