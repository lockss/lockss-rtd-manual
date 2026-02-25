============================
Creating the ``lockss`` User
============================

.. note::

   Commands in this section are run as ``root`` .

This section describes how to create the ``lockss`` system user (if necessary), under which the :term:`LOCKSS stack` will run.

Follow these steps:

1. Check if the ``lockss`` user already exists. Run this :program:`id` command as ``root``:

   .. code-block:: shell

      id lockss

   *  If a ``lockss`` user already exists on the host, the :program:`id` command will output the information associated with it, including its user ID (``uid``) and group ID (``gid``), for example:

      .. code-block:: text

         uid=958(lockss) gid=958(lockss) groups=958(lockss)

      In this case, no further action is needed in this section, and you can proceed to :numref:`Downloading the LOCKSS Installer` (the next section (:ref:`Downloading the LOCKSS Installer`).

   *  Otherwise, the :program:`id` command above will output an error message, for example:

      .. code-block:: text

         id: ‘lockss’: no such user

      In this case, you will need to create a ``lockss`` user on the host now, by going on to the next step.

2. If the ``lockss`` user needs to be created, run this :program:`useradd` command as ``root``:

   .. code-block:: shell

      useradd --system --user-group --create-home --shell=/bin/bash lockss

   or equivalently:

   .. code-block:: shell

      useradd -rUms /bin/bash lockss

   This will create a ``lockss`` system user, a ``lockss`` system group, and a home directory in :file:`{$HOME}/lockss` (which is :file:`/home/lockss` on most Linux systems).
