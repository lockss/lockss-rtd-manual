==========================
Installing :program:`wget`
==========================

Downloading and running the LOCKSS Installer requires either :program:`curl` or :program:`wget`. Most typical Linux systems have at least one installed by default. You can check by typing ``curl --version`` or ``wget --version`` and verifying that the output is not an error message. This section describes how to install :program:`wget` if necessary. (If you prefer to install :program:`curl`, see :doc:`curl`.)

Select your operating system below and follow the instructions as root [#fnroot]_:

.. COMMENT OSTABS

.. tab-set::
   :class: sd-bg-light

   .. tab-item:: AlmaLinux
      :sync: alma

      .. include:: wget-dnf.rst

   .. tab-item:: Arch Linux
      :sync: arch

      .. include:: wget-pacman.rst

   .. tab-item:: CentOS
      :sync: centos

      .. tab-set::

         .. tab-item:: CentOS Stream
            :sync: centosstream

            .. include:: wget-dnf.rst

         .. tab-item:: CentOS 7
            :sync: centos7

            .. include:: wget-yum.rst

   .. tab-item:: Debian
      :sync: debian

      .. include:: wget-apt.rst

   .. tab-item:: EuroLinux
      :sync: eurolinux

      .. tab-set::

         .. tab-item:: EuroLinux 8
            :sync: eurolinux8

            .. include:: wget-dnf.rst

         .. tab-item:: EuroLinux 7
            :sync: eurolinux7

            .. include:: wget-yum.rst

   .. tab-item:: Fedora Linux
      :sync: fedora

      .. include:: wget-dnf.rst

   .. tab-item:: Linux Mint
      :sync: mint

      .. include:: wget-apt.rst

   .. tab-item:: OpenSUSE
      :sync: opensuse

      .. tab-set::

         .. tab-item:: OpenSUSE Tumbleweed
            :sync: opensusetumbleweed

            .. include:: wget-zypper.rst

         .. tab-item:: OpenSUSE Leap
            :sync: opensuseleap

            .. include:: wget-zypper.rst

   .. tab-item:: Oracle Linux
      :sync: oracle

      .. tab-set::

         .. tab-item:: Oracle Linux 8-9
            :sync: oracle8

            .. include:: wget-dnf.rst

         .. tab-item:: Oracle Linux 7
            :sync: oracle7

            .. include:: wget-yum.rst

   .. tab-item:: RHEL
      :sync: rhel

      .. tab-set::

         .. tab-item:: RHEL 8-9
            :sync: rhel8

            .. include:: wget-dnf.rst

         .. tab-item:: RHEL 7
            :sync: rhel7

            .. include:: wget-yum.rst

   .. tab-item:: Rocky Linux
      :sync: rocky

      .. include:: wget-dnf.rst

   .. tab-item:: Scientific Linux
      :sync: scientific

      .. include:: wget-yum.rst

   .. tab-item:: Ubuntu
      :sync: ubuntu

      .. include:: wget-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
