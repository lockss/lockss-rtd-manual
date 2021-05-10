==============
Installing Git
==============

`Git <https://git-scm.com/>`_ is a version control system, used to interact with code repositories.

The `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ is available from `GitHub <https://github.com>`_, and you will need a Git client to download it.

----------------
Checking for Git
----------------

Your operating system may already be equipped with a Git client. Type:

.. code-block:: shell

   git --version

If the output is a version number, for example:

.. code-block:: text

   git version 2.31.1

then Git is installed correctly and you do not need to take further action.

If you see an error message similar to the following:

.. code-block:: text

   bash: git: command not found

then you need to install Git.

-------------------------------------
Installing Git With a Package Manager
-------------------------------------

On many flavors of Linux, you can install Git with a built-in package manager (Apt, Dnf, Pacman, Yum, Zypper, etc.). Select your operating system below for instructions on how to install Git:

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
