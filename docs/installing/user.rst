============================
Creating the ``lockss`` User
============================

.. note::

   Commands in this section are run as ``root``  [#fnroot]_.

The LOCKSS system runs under a system user named ``lockss``, in a system group named ``lockss``.

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
