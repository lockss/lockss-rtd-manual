==============
Installing Git
==============

`Git <https://git-scm.com/>`_ is a version control system, used to interact with code repositories. The `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ is available from `GitHub <https://github.com>`_, and you will need a Git client to download it.

Follow these instructions to install Git:

1. Run this command (as any user):

   .. code-block:: shell

      git --version

2. If the output is a version number (for example ``git version 2.31.1``), Git is already installed; however if you see an error message (for example ``bash: git: command not found``), follow the instructions corresponding to your operating system below to install Git as ``root`` [#fnroot]_:

   .. tab-set::

      .. tab-item:: AlmaLinux

         .. include:: git-dnf.rst

      .. tab-item:: Arch Linux

         .. include:: git-pacman.rst

      .. tab-item:: CentOS

         .. tab-set::

            .. tab-item:: CentOS 7

               .. include:: git-yum.rst

            .. tab-item:: CentOS 8

               .. include:: git-dnf.rst

      .. tab-item:: Debian

         .. include:: git-apt.rst

      .. tab-item:: Fedora

         .. include:: git-dnf.rst

      .. tab-item:: Linux Mint

         .. include:: git-apt.rst

      .. tab-item:: OpenSUSE

         .. include:: git-zypper.rst

      .. tab-item:: Oracle Linux

         .. tab-set::

            .. tab-item:: Oracle Linux 7

               .. include:: git-yum.rst

            .. tab-item:: Oracle Linux 8

               .. include:: git-dnf.rst

      .. tab-item:: RHEL

         .. tab-set::

            .. tab-item:: RHEL 7

               .. include:: git-yum.rst

            .. tab-item:: RHEL 8

               .. include:: git-dnf.rst

      .. tab-item:: Rocky Linux

         .. include:: git-dnf.rst

      .. tab-item:: Ubuntu

         .. include:: git-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
