=========================
Installing :program:`tar`
=========================

Installing LOCKSS |LATEST_MINOR| requires :program:`tar` (or :program:`gtar`). This utility is installed out of the box in almost all Linux operating systems, but in the event it is not, this section explains how to install it.

Type ``tar --version`` (or ``gtar --version``) at the host's command line. If an error message like ``bash: tar: command not found`` is output, select your operating system below and follow the instructions as ``root`` [#fnroot]_:

.. COMMENT OSTABS

.. tab-set::

   .. tab-item:: AlmaLinux OS
      :sync: almalinux-os

      .. include:: tar-dnf.rst

   .. tab-item:: Arch Linux
      :sync: arch-linux

      .. include:: tar-pacman.rst

   .. tab-item:: CentOS Stream
      :sync: centos-stream

      .. include:: tar-dnf.rst

   .. tab-item:: Debian
      :sync: debian

      .. include:: tar-apt.rst

   .. tab-item:: Fedora Linux
      :sync: fedora-linux

      .. include:: tar-dnf.rst

   .. tab-item:: Linux Mint
      :sync: linux-mint

      .. include:: tar-apt.rst

   .. tab-item:: OpenSUSE Leap
      :sync: opensuse-leap

      .. include:: tar-zypper.rst

   .. tab-item:: OpenSUSE Tumbleweed
      :sync: opensuse-tumbleweed

      .. include:: tar-zypper.rst

   .. tab-item:: Oracle Linux
      :sync: oracle-linux

      .. include:: tar-dnf.rst

   .. tab-item:: Red Hat Enterprise Linux
      :sync: rhel

      .. include:: tar-dnf.rst

   .. tab-item:: Rocky Linux
      :sync: rocky-linux

      .. include:: tar-dnf.rst

   .. tab-item:: SUSE Linux Enterprise Server
      :sync: sles

      .. include:: tar-zypper.rst

   .. tab-item:: Ubuntu
      :sync: ubuntu

      .. include:: tar-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
