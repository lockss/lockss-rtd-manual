=================
Installing HTTPie
=================

:doc:`/installing/downloading` requires `Curl <https://curl.se/>`_, `Wget <https://www.gnu.org/software/wget/>`_ or `HTTPie <https://httpie.io/>`_. Most typical Linux systems have at least one installed by default. You can check by typing ``curl --version``, ``wget --version`` or ``http --version`` at the command line and verifying that at least one of them outputs a valid version message (meaning the corresponding software is installed). This section describes how to install `HTTPie <https://httpie.io/>`_ if necessary.

Select your operating system below and follow the instructions as root [#fnroot]_:

.. COMMENT OSTABS

.. tab-set::
   :class: sd-bg-light

   .. tab-item:: AlmaLinux OS
      :sync: alma

      .. include:: httpie-dnf.rst

   .. tab-item:: Arch Linux
      :sync: arch

      .. include:: httpie-pacman.rst

   .. tab-item:: CentOS Stream
      :sync: centos-stream

      .. include:: httpie-dnf.rst

   .. tab-item:: Debian
      :sync: debian

      .. include:: httpie-apt.rst

   .. tab-item:: Fedora Linux
      :sync: fedora

      .. include:: httpie-dnf.rst

   .. tab-item:: Linux Mint
      :sync: mint

      .. include:: httpie-apt.rst

   .. tab-item:: OpenSUSE
      :sync: opensuse

      .. tab-set::

         .. tab-item:: OpenSUSE Tumbleweed
            :sync: opensuse-tumbleweed

            .. include:: httpie-zypper.rst

         .. tab-item:: OpenSUSE Leap
            :sync: opensuse-leap

            .. include:: httpie-zypper.rst

   .. tab-item:: Oracle Linux
      :sync: oracle

      .. include:: httpie-dnf.rst

   .. tab-item:: Red Hat Enterprise Linux
      :sync: rhel

      .. include:: httpie-dnf.rst

   .. tab-item:: Rocky Linux
      :sync: rocky

      .. include:: httpie-dnf.rst

   .. tab-item:: SUSE Linux Enterprise Server
      :sync: sles

      .. include:: httpie-zypper.rst

   .. tab-item:: Ubuntu
      :sync: ubuntu

      .. include:: httpie-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
