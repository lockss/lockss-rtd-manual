============================
Creating the ``lockss`` User
============================

The LOCKSS system runs under a system user named ``lockss``.

Run this :program:`useradd` command as ``root`` [#fnroot]_ :

.. code-block:: shell

   useradd --system --user-group --create-home --shell=/bin/bash lockss

or equivalently:

.. code-block:: shell

   useradd -rUms /bin/bash lockss

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/appendix/root`.
