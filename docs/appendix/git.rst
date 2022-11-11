==============
Installing Git
==============

`Git <https://git-scm.com/>`_ is a version control system, used to interact with code repositories. The `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ is available from `GitHub <https://github.com>`_, and you will need a Git client to download it.

Follow these instructions to install Git:

1. Run this command (as any user):

   .. code-block:: shell

      git --version

2. If the output is a version number (for example ``git version 2.31.1``), Git is already installed; however if you see an error message (for example ``bash: git: command not found``), follow the instructions corresponding to your operating system below to install Git as ``root`` [#fnroot]_:

   .. COMMENT OSTABS

   .. tab-set::

      .. tab-item:: AlmaLinux
         :sync: alma

         .. include:: git-dnf.rst

      .. tab-item:: Arch Linux
         :sync: arch

         .. include:: git-pacman.rst

      .. tab-item:: CentOS
         :sync: centos

         .. tab-set::

            .. tab-item:: CentOS Stream
               :sync: centosstream

               .. include:: git-dnf.rst

            .. tab-item:: CentOS 7
               :sync: centos7

               .. include:: git-yum.rst

      .. tab-item:: Debian
         :sync: debian

         .. include:: git-apt.rst

      .. tab-item:: EuroLinux
         :sync: eurolinux

         .. tab-set::

            .. tab-item:: EuroLinux 8-9
               :sync: eurolinux8

               .. include:: git-dnf.rst

            .. tab-item:: EuroLinux 7
               :sync: eurolinux7

               .. include:: git-yum.rst

      .. tab-item:: Fedora Linux
         :sync: fedora

         .. include:: git-dnf.rst

      .. tab-item:: Linux Mint
         :sync: mint

         .. include:: git-apt.rst

      .. tab-item:: OpenSUSE
         :sync: opensuse

         .. tab-set::

            .. tab-item:: OpenSUSE Tumbleweed
               :sync: opensusetumbleweed

               .. include:: git-zypper.rst

            .. tab-item:: OpenSUSE Leap
               :sync: opensuseleap

               .. include:: git-zypper.rst

      .. tab-item:: Oracle Linux
         :sync: oracle

         .. tab-set::

            .. tab-item:: Oracle Linux 8-9
               :sync: oracle8

               .. include:: git-dnf.rst

            .. tab-item:: Oracle Linux 7
               :sync: oracle7

               .. include:: git-yum.rst

      .. tab-item:: RHEL
         :sync: rhel

         .. tab-set::

            .. tab-item:: RHEL 8-9
               :sync: rhel8

               .. include:: git-dnf.rst

            .. tab-item:: RHEL 7
               :sync: rhel7

               .. include:: git-yum.rst

      .. tab-item:: Rocky Linux
         :sync: rocky

         .. include:: git-dnf.rst

      .. tab-item:: Scientific Linux
         :sync: scientific

         .. include:: git-yum.rst

      .. tab-item:: Ubuntu
         :sync: ubuntu

         .. include:: git-apt.rst

----

.. rubric:: Footnotes

.. [#fnroot]

   See :doc:`/sysadmin/root`.
