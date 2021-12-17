==============
Installing Git
==============

`Git <https://git-scm.com/>`_ is a version control system, used to interact with code repositories. The `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ is available from `GitHub <https://github.com>`_, and you will need a Git client to download it.

Follow these instructions to install Git:

1. Run this command (as any user):

   .. code-block:: shell

      git --version

2. If the output is a version number (for example ``git version 2.31.1``), Git is already installed; however if you see an error message (for example ``bash: git: command not found``), follow the instructions corresponding to your operating system below to install Git as ``root`` [#fnroot]_:

   .. tabs::

      .. group-tab:: AlmaLinux

         .. include:: git-dnf.rst

      .. group-tab:: Arch Linux

         .. include:: git-pacman.rst

      .. group-tab:: CentOS

         .. tabs::

            .. group-tab:: CentOS 7

               .. include:: git-yum.rst

            .. group-tab:: CentOS 8

               .. include:: git-dnf.rst

      .. group-tab:: Debian

         .. include:: git-apt.rst

      .. group-tab:: Fedora

         .. include:: git-dnf.rst

      .. group-tab:: Linux Mint

         .. include:: git-apt.rst

      .. group-tab:: OpenSUSE

         .. include:: git-zypper.rst

      .. group-tab:: Oracle Linux

         .. tabs::

            .. group-tab:: Oracle Linux 7

               .. include:: git-yum.rst

            .. group-tab:: Oracle Linux 8

               .. include:: git-dnf.rst

      .. group-tab:: RHEL

         .. tabs::

            .. group-tab:: RHEL 7

               .. include:: git-yum.rst

            .. group-tab:: RHEL 8

               .. include:: git-dnf.rst

      .. group-tab:: Rocky Linux

         .. include:: git-dnf.rst

      .. group-tab:: Ubuntu

         .. include:: git-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/appendix/root`.
