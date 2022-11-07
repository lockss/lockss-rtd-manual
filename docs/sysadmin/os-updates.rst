========================
Operating System Updates
========================

You will want to update your Linux operating system at different times:

*  Before :doc:`/upgrading/index`.

*  Before :doc:`/installing/index` for the first time.

*  When security-related updates are released for the Linux kernel (which requires rebooting the machine) or other installed software packages.

Your system may be set up for automatic updates or your system administrator may have policies for which packages can be udpated and when.

If you wish to update software packages manually, select your operating system below and follow the instructions as ``root`` [#fnroot]_:

.. tab-set::
   :class: sd-bg-light

   .. tab-item:: AlmaLinux
      :sync: alma

      .. include:: os-updates-dnf.rst

   .. tab-item:: Arch Linux
      :sync: arch

      .. include:: os-updates-pacman.rst

   .. tab-item:: CentOS
      :sync: centos

      .. tab-set::

         .. tab-item:: CentOS 7
            :sync: centos7

            .. include:: os-updates-yum.rst

         .. tab-item:: CentOS 8
            :sync: centos8

            .. include:: os-updates-dnf.rst

         .. tab-item:: CentOS Stream 8-9
            :sync: centosstream8

            .. include:: os-updates-dnf.rst

   .. tab-item:: Debian
      :sync: debian

      .. include:: os-updates-apt.rst

   .. tab-item:: EuroLinux
      :sync: eurolinux

      .. tab-set::

         .. tab-item:: EuroLinux 7
            :sync: eurolinux7

            .. include:: os-updates-yum.rst

         .. tab-item:: EuroLinux 8
            :sync: eurolinux8

            .. include:: os-updates-dnf.rst

   .. tab-item:: Fedora
      :sync: fedora

      .. include:: os-updates-dnf.rst

   .. tab-item:: Linux Mint
      :sync: mint

      .. include:: os-updates-apt.rst

   .. tab-item:: OpenSUSE
      :sync: opensuse

      .. tab-set::

         .. tab-item:: OpenSUSE Leap 15
            :sync: opensuse15

            .. include:: os-updates-zypper.rst

         .. tab-item:: OpenSUSE Tumbleweed
            :sync: opensusetumbleweed

            .. include:: os-updates-zypper.rst

   .. tab-item:: Oracle Linux
      :sync: oracle

      .. tab-set::

         .. tab-item:: Oracle Linux 7
            :sync: oracle7

            .. include:: os-updates-yum.rst

         .. tab-item:: Oracle Linux 8
            :sync: oracle8

            .. include:: os-updates-dnf.rst

   .. tab-item:: RHEL
      :sync: rhel

      .. tab-set::

         .. tab-item:: RHEL 7
            :sync: rhel7

            .. include:: os-updates-yum.rst

         .. tab-item:: RHEL 8
            :sync: rhel8

            .. include:: os-updates-dnf.rst

   .. tab-item:: Rocky Linux
      :sync: rocky

      .. include:: os-updates-dnf.rst

   .. tab-item:: Scientific Linux
      :sync: scientific

      .. include:: os-updates-yum.rst

   .. tab-item:: Ubuntu
      :sync: ubuntu

      .. include:: os-updates-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
