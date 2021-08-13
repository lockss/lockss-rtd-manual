==========================
Installing :program:`wget`
==========================

Downloading and running the LOCKSS Installer requires either :program:`curl` or :program:`wget`. Most typical Linux systems have at least one installed by default. You can check by typing ``curl --version`` or ``wget --version`` and verifying that the output is not an error message. This section describes how to install :program:`wget` if necessary. (If you prefer to install :program:`curl`, see :doc:`curl`.)

Select your operating system below and follow the instructions as root [#fnroot]_:

.. tabs::

   .. group-tab:: AlmaLinux

      .. include:: wget-dnf.rst

   .. group-tab:: Arch Linux

      .. include:: wget-pacman.rst

   .. group-tab:: CentOS

      .. tabs::

         .. group-tab:: CentOS 7

            .. include:: wget-yum.rst

         .. group-tab:: CentOS 8

            .. include:: wget-dnf.rst

   .. group-tab:: Debian

      .. include:: wget-apt.rst

   .. group-tab:: Fedora

      .. include:: wget-dnf.rst

   .. group-tab:: Linux Mint

      .. include:: wget-apt.rst

   .. group-tab:: OpenSUSE

      .. include:: wget-zypper.rst

   .. group-tab:: Oracle Linux

      .. tabs::

         .. group-tab:: Oracle Linux 7

            .. include:: wget-yum.rst

         .. group-tab:: Oracle Linux 8

            .. include:: wget-dnf.rst

   .. group-tab:: RHEL

      .. tabs::

         .. group-tab:: RHEL 7

            .. include:: wget-yum.rst

         .. group-tab:: RHEL 8

            .. include:: wget-dnf.rst

   .. group-tab:: Rocky Linux

      .. include:: wget-dnf.rst

   .. group-tab:: Ubuntu

      .. include:: wget-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/appendix/root`.
