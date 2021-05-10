============================
Creating the ``lockss`` User
============================

The LOCKSS system runs under a system user named ``lockss``, which is in a system group named ``lockss``.

To create the ``lockss`` user and group, run this :program:`useradd` command as ``root`` [#fnroot]_ :

.. code-block:: shell

   useradd --system --user-group --create-home --shell=/bin/false lockss

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/appendix/root`.
