========================
Operating System Updates
========================

You will want to update your Linux operating system at different times:

*  Before :doc:`/upgrading/index`.

*  Before :doc:`/installing/index` for the first time.

*  When security-related updates are released for the Linux kernel (which requires rebooting the machine) or other installed software packages.

Your system may be set up for automatic updates or your system administrator may have policies for which packages can be udpated and when.

If you wish to update software packages manually, select your operating system below and follow the instructions as ``root`` [#fnroot]_:

.. tabs::

   .. group-tab:: AlmaLinux

      .. include:: os-updates-dnf.rst

   .. group-tab:: Arch Linux

      .. include:: os-updates-pacman.rst

   .. group-tab:: CentOS

      .. tabs::

         .. group-tab:: CentOS 7

            .. include:: os-updates-yum.rst

         .. group-tab:: CentOS 8

            .. include:: os-updates-dnf.rst

         .. group-tab:: CentOS Stream

            .. include:: os-updates-dnf.rst

   .. group-tab:: Debian

      .. include:: os-updates-apt.rst

   .. group-tab:: EuroLinux

      .. tabs::

         .. group-tab:: EuroLinux 7

            .. include:: os-updates-yum.rst

         .. group-tab:: EuroLinux 8

            .. include:: os-updates-dnf.rst

   .. group-tab:: Fedora

      .. include:: os-updates-dnf.rst

   .. group-tab:: Linux Mint

      .. include:: os-updates-apt.rst

   .. group-tab:: OpenSUSE

      .. tabs::

         .. group-tab:: OpenSUSE Leap 15

            .. include:: os-updates-zypper.rst

         .. group-tab:: OpenSUSE Tumbleweed

            .. include:: os-updates-zypper.rst

   .. group-tab:: Oracle Linux

      .. tabs::

         .. group-tab:: Oracle Linux 7

            .. include:: os-updates-yum.rst

         .. group-tab:: Oracle Linux 8

            .. include:: os-updates-dnf.rst

   .. group-tab:: RHEL

      .. tabs::

         .. group-tab:: RHEL 7

            .. include:: os-updates-yum.rst

         .. group-tab:: RHEL 8

            .. include:: os-updates-dnf.rst

   .. group-tab:: Rocky Linux

      .. include:: os-updates-dnf.rst

   .. group-tab:: Scientific Linux

      .. include:: os-updates-yum.rst

   .. group-tab:: Ubuntu

      .. include:: os-updates-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
