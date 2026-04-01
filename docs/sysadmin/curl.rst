===============
Installing Curl
===============

:doc:`/installing/downloading` and :doc:`/installing/running` require :term:`Curl` or :term:`Wget`. Most typical Linux systems have at least one installed by default. You can check by typing ``curl --version`` and ``wget --version`` at the command line and verifying that at least one of them outputs a valid version message (meaning the corresponding software is installed). This section describes how to install `Curl <https://curl.se/>`_ if necessary.

Select your operating system below and follow the instructions as ``root`` [#fnroot]_:

.. COMMENT OSTABS

.. tab-set::

   .. tab-item:: AlmaLinux OS
      :sync: almalinux-os

      .. include:: curl-dnf.rst

   .. tab-item:: Arch Linux
      :sync: arch-linux

      .. include:: curl-pacman.rst

   .. tab-item:: CentOS Stream
      :sync: centos-stream

      .. include:: curl-dnf.rst

   .. tab-item:: Debian
      :sync: debian

      .. include:: curl-apt.rst

   .. tab-item:: Fedora Linux
      :sync: fedora-linux

      .. include:: curl-dnf.rst

   .. tab-item:: Linux Mint
      :sync: linux-mint

      .. include:: curl-apt.rst

   .. tab-item:: OpenSUSE Leap
      :sync: opensuse-leap

      .. include:: curl-zypper.rst

   .. tab-item:: OpenSUSE Tumbleweed
      :sync: opensuse-tumbleweed

      .. include:: curl-zypper.rst

   .. tab-item:: Oracle Linux
      :sync: oracle-linux

      .. include:: curl-dnf.rst

   .. tab-item:: Red Hat Enterprise Linux
      :sync: rhel

      .. include:: curl-dnf.rst

   .. tab-item:: Rocky Linux
      :sync: rocky-linux

      .. include:: curl-dnf.rst

   .. tab-item:: SUSE Linux Enterprise Server
      :sync: sles

      .. include:: curl-zypper.rst

   .. tab-item:: Ubuntu
      :sync: ubuntu

      .. include:: curl-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
