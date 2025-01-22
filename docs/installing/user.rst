============================
Creating the ``lockss`` User
============================

.. rubric:: Section Summary

The first task is to create a system user named ``lockss``, under which the LOCKSS system will run.

.. note::

   Commands in this section are run as ``root``  [#fnroot]_.

To create the ``lockss`` user, follow these steps:

1. Run this :program:`id` command as ``root`` [#fnroot]_:

   .. code-block:: shell

      id lockss

   If a ``lockss`` user already exists on the host, the :program:`id` command will output the information associated with it, including its user ID (``uid``) and group ID (``gid``), for example:

   .. code-block:: text

      uid=958(lockss) gid=958(lockss) groups=958(lockss)

   and you do not need to create a ``lockss`` user on the host again.

2.  Otherwise, the :program:`id` command will output an error, for example:

   .. code-block:: text

      id: ‘lockss’: no such user

   and you will need to create a ``lockss`` user on the host now. To do so, run this :program:`useradd` command as ``root`` [#fnroot]_:

   .. code-block:: shell

      useradd --system --user-group --create-home --shell=/bin/bash lockss

   or equivalently:

   .. code-block:: shell

      useradd -rUms /bin/bash lockss

   This will create a ``lockss`` system user, a ``lockss`` system group, and a home directory in :file:`/home/lockss`.

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
