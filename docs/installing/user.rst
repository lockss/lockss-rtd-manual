.. _Creating the lockss User and Group:

======================================
Creating the ``lockss`` User and Group
======================================

This section describes how to create the ``lockss`` system user and group (if necessary), under which the :term:`LOCKSS stack` will run.

.. _Establishing a root Session:

-------------------------------
Establishing a ``root`` Session
-------------------------------

The configuration and operation of LOCKSS entail commands run as ``lockss``, but the installation of LOCKSS is largely done as ``root``. We recommend opening a ``root`` console session and using it throughout this chapter. At first, this ``root`` session does not need to be in any particular directory.

.. _Invoking adduser:

---------------------------
Invoking :program:`adduser`
---------------------------

To create the ``lockss`` user and group, follow these steps:

1. .. index:: whoami

   Double-check that you are operating in the ``root`` session established for the entirety of this chapter [#fn-root-session]_ by typing:

   .. code-block:: shell

      whoami

   and verifying that the output is ``root``.

2. .. index:: id

   Check if the ``lockss`` user already exists. Run this :program:`id` command:

   .. code-block:: shell

      id lockss

   *  If the :program:`id` command outputs information about the ``lockss`` user including its user ID (UID) and group ID (GID), for example:

      .. code-block:: text

         uid=958(lockss) gid=958(lockss) groups=958(lockss)

      then the ``lockss`` user already exists on the host, and you can proceed to :octicon:`diff-renamed` :numref:`Downloading the LOCKSS Installer` (:ref:`Downloading the LOCKSS Installer`).

   *  If the :program:`id` command outputs an error message, for example:

      .. code-block:: text

         id: ‘lockss’: no such user

      then the ``lockss`` user does not exist on the host yet, and you will need to it below.

3. .. index:: useradd

   If the ``lockss`` user needs to be created on the host, run this :program:`useradd` command:

   .. code-block:: shell

      useradd --system --user-group --create-home --shell=/bin/bash lockss

   or equivalently:

   .. code-block:: shell

      useradd -rUms /bin/bash lockss

   This will create a ``lockss`` system user, a ``lockss`` system group, and a home directory in (typically) :file:`/home/lockss`.

----

.. rubric:: Footnotes

.. [#fn-root-session]

   See :numref:`Establishing a root Session` (:ref:`Establishing a root Session`).
