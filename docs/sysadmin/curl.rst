==========================
Installing :program:`curl`
==========================

Downloading and running the LOCKSS Installer requires either :program:`curl` or :program:`wget`. Most typical Linux systems have at least one installed by default. You can check by typing ``curl --version`` or ``wget --version`` and verifying that the output is not an error message. This section describes how to install :program:`curl` if necessary. (If you prefer to install :program:`wget`, see :doc:`wget`.)

Select your operating system below and follow the instructions as root [#fnroot]_:

.. tabs::

   .. group-tab:: AlmaLinux

      .. include:: curl-dnf.rst

   .. group-tab:: Arch Linux

      .. include:: curl-pacman.rst

   .. group-tab:: CentOS

      .. tabs::

         .. group-tab:: CentOS 7

            .. include:: curl-yum.rst

         .. group-tab:: CentOS 8

            .. include:: curl-dnf.rst

         .. group-tab:: CentOS Stream

            .. include:: curl-dnf.rst

   .. group-tab:: Debian

      .. include:: curl-apt.rst

   .. group-tab:: EuroLinux

      .. tabs::

         .. group-tab:: EuroLinux 7

            .. include:: curl-yum.rst

         .. group-tab:: EuroLinux 8

            .. include:: curl-dnf.rst

   .. group-tab:: Fedora

      .. include:: curl-dnf.rst

   .. group-tab:: Linux Mint

      .. include:: curl-apt.rst

   .. group-tab:: OpenSUSE

      .. tabs::

         .. group-tab:: OpenSUSE Leap 15

            .. include:: curl-zypper.rst

         .. group-tab:: OpenSUSE Tumbleweed

            .. include:: curl-zypper.rst

   .. group-tab:: Oracle Linux

      .. tabs::

         .. group-tab:: Oracle Linux 7

            .. include:: curl-yum.rst

         .. group-tab:: Oracle Linux 8

            .. include:: curl-dnf.rst

   .. group-tab:: RHEL

      .. tabs::

         .. group-tab:: RHEL 7

            .. include:: curl-yum.rst

         .. group-tab:: RHEL 8

            .. include:: curl-dnf.rst

   .. group-tab:: Rocky Linux

      .. include:: curl-dnf.rst

   .. group-tab:: Scientific Linux

      .. include:: curl-yum.rst

   .. group-tab:: Ubuntu

      .. include:: curl-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
