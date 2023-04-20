===============
Installing Curl
===============

:doc:`/installing/downloading` requires `Curl <https://curl.se/>`_, `Wget <https://www.gnu.org/software/wget/>`_ or `HTTPie <https://httpie.io/>`_. Most typical Linux systems have at least one installed by default. You can check by typing ``curl --version``, ``wget --version`` or ``http --version``, and seeing which ones do not output an error message.

This section describes how to install `Curl <https://curl.se/>`_ if necessary.

Select your operating system below and follow the instructions as root [#fnroot]_:

.. COMMENT OSTABS

.. tab-set::
   :class: sd-bg-light

   .. tab-item:: AlmaLinux OS
      :sync: alma

      .. include:: curl-dnf.rst

   .. tab-item:: Arch Linux
      :sync: arch

      .. include:: curl-pacman.rst

   .. tab-item:: CentOS
      :sync: centos

      .. tab-set::

         .. tab-item:: CentOS Stream
            :sync: centosstream

            .. include:: curl-dnf.rst

         .. tab-item:: CentOS 7
            :sync: centos7

            .. include:: curl-yum.rst

   .. tab-item:: Debian
      :sync: debian

      .. include:: curl-apt.rst

   .. tab-item:: EuroLinux
      :sync: eurolinux

      .. tab-set::

         .. tab-item:: EuroLinux 8-9
            :sync: eurolinux8

            .. include:: curl-dnf.rst

         .. tab-item:: EuroLinux 7
            :sync: eurolinux7

            .. include:: curl-yum.rst

   .. tab-item:: Fedora Linux
      :sync: fedora

      .. include:: curl-dnf.rst

   .. tab-item:: Linux Mint
      :sync: mint

      .. include:: curl-apt.rst

   .. tab-item:: OpenSUSE
      :sync: opensuse

      .. tab-set::

         .. tab-item:: OpenSUSE Tumbleweed
            :sync: opensusetumbleweed

            .. include:: curl-zypper.rst

         .. tab-item:: OpenSUSE Leap
            :sync: opensuseleap

            .. include:: curl-zypper.rst

   .. tab-item:: Oracle Linux
      :sync: oracle

      .. tab-set::

         .. tab-item:: Oracle Linux 8-9
            :sync: oracle8

            .. include:: curl-dnf.rst

         .. tab-item:: Oracle Linux 7
            :sync: oracle7

            .. include:: curl-yum.rst

   .. tab-item:: RHEL
      :sync: rhel

      .. tab-set::

         .. tab-item:: RHEL 8-9
            :sync: rhel8

            .. include:: curl-dnf.rst

         .. tab-item:: RHEL 7
            :sync: rhel7

            .. include:: curl-yum.rst

   .. tab-item:: Rocky Linux
      :sync: rocky

      .. include:: curl-dnf.rst

   .. tab-item:: Scientific Linux
      :sync: scientific

      .. include:: curl-yum.rst

   .. tab-item:: Ubuntu
      :sync: ubuntu

      .. include:: curl-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
