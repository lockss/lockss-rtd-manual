===========================
Installing :program:`unzip`
===========================

Installing LOCKSS |LATEST_MINOR| requires :program:`unzip`. This utility is installed out of the box in almost all Linux operating systems, but in the event it is not, this section explains how to install it.

Type ``unzip --version`` at the host's command line. If an error message like ``bash: unzip: command not found`` is output, select your operating system below and follow the instructions as ``root`` [#fnroot]_:

.. COMMENT OSTABS

.. tab-set::

   .. tab-item:: AlmaLinux OS
      :sync: almalinux-os

      .. include:: unzip-dnf.rst

   .. tab-item:: Arch Linux
      :sync: arch-linux

      .. include:: unzip-pacman.rst

   .. tab-item:: CentOS Stream
      :sync: centos-stream

      .. include:: unzip-dnf.rst

   .. tab-item:: Debian
      :sync: debian

      .. include:: unzip-apt.rst

   .. tab-item:: Fedora Linux
      :sync: fedora-linux

      .. include:: unzip-dnf.rst

   .. tab-item:: Linux Mint
      :sync: linux-mint

      .. include:: unzip-apt.rst

   .. tab-item:: OpenSUSE Leap
      :sync: opensuse-leap

      .. include:: unzip-zypper.rst

   .. tab-item:: OpenSUSE Tumbleweed
      :sync: opensuse-tumbleweed

      .. include:: unzip-zypper.rst

   .. tab-item:: Oracle Linux
      :sync: oracle-linux

      .. include:: unzip-dnf.rst

   .. tab-item:: Red Hat Enterprise Linux
      :sync: rhel

      .. include:: unzip-dnf.rst

   .. tab-item:: Rocky Linux
      :sync: rocky-linux

      .. include:: unzip-dnf.rst

   .. tab-item:: SUSE Linux Enterprise Server
      :sync: sles

      .. include:: unzip-zypper.rst

   .. tab-item:: Ubuntu
      :sync: ubuntu

      .. include:: unzip-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
