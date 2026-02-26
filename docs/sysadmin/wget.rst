===============
Installing Wget
===============

:doc:`/installing/downloading` and :doc:`/installing/running` require `Curl <https://curl.se/>`_ or `Wget <https://www.gnu.org/software/wget/>`_. Most typical Linux systems have at least one installed by default. You can check by typing ``curl --version`` and ``wget --version`` at the command line and verifying that at least one of them outputs a valid version message (meaning the corresponding software is installed). This section describes how to install `Wget <https://www.gnu.org/software/wget/>`_ if necessary.

Select your operating system below and follow the instructions as ``root`` [#fnroot]_:

.. COMMENT OSTABS

.. tab-set::

   .. tab-item:: AlmaLinux OS
      :sync: alma

      .. include:: wget-dnf.rst

   .. tab-item:: Arch Linux
      :sync: arch

      .. include:: wget-pacman.rst

   .. tab-item:: CentOS Stream
      :sync: centos-stream

      .. include:: wget-dnf.rst

   .. tab-item:: Debian
      :sync: debian

      .. include:: wget-apt.rst

   .. tab-item:: Fedora Linux
      :sync: fedora

      .. include:: wget-dnf.rst

   .. tab-item:: Linux Mint
      :sync: mint

      .. include:: wget-apt.rst

   .. tab-item:: OpenSUSE
      :sync: opensuse

      .. tab-set::

         .. tab-item:: OpenSUSE Leap
            :sync: opensuse-leap

            .. include:: wget-zypper.rst

         .. tab-item:: OpenSUSE Tumbleweed
            :sync: opensuse-tumbleweed

            .. include:: wget-zypper.rst

   .. tab-item:: Oracle Linux
      :sync: oracle

      .. include:: wget-dnf.rst

   .. tab-item:: Red Hat Enterprise Linux
      :sync: rhel

      .. include:: wget-dnf.rst

   .. tab-item:: Rocky Linux
      :sync: rocky

      .. include:: wget-dnf.rst

   .. tab-item:: SUSE Linux Enterprise Server
      :sync: sles

      .. include:: wget-zypper.rst

   .. tab-item:: Ubuntu
      :sync: ubuntu

      .. include:: wget-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
