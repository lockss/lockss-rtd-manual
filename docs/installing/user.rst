============================
Creating the ``lockss`` User
============================

.. note::

   Commands in this section are run as ``root``  [#fnroot]_.

The first task is to create a system user named ``lockss``, under which the LOCKSS system will run.

Run this :program:`useradd` command as ``root`` [#fnroot]_ :

.. code-block:: shell

   useradd --system --user-group --create-home --shell=/bin/bash lockss

or equivalently:

.. code-block:: shell

   useradd -rUms /bin/bash lockss

This will create a ``lockss`` system user, a ``lockss`` system group, and a home directory in :file:`/home/lockss`.

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/appendix/root`.
