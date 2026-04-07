==============
Installing Git
==============

`Git <https://git-scm.com/>`_ is a version control system, used to interact with code repositories. The `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ is available from `GitHub <https://github.com>`_, and you will need a Git client to download it.

Follow these instructions to install Git:

1. Run this command (as any user):

   .. code-block:: shell

      git --version

2. If the output is a version number (for example ``git version 2.31.1``), Git is already installed; however if you see an error message (for example ``bash: git: command not found``), follow the instructions corresponding to your operating system below to install Git as ``root``:

   .. COMMENT OSTABS

   .. tab-set::

      .. tab-item:: AlmaLinux OS
         :sync: almalinux-os

         .. include:: git-dnf.rst

      .. tab-item:: Arch Linux
         :sync: arch-linux

         .. include:: git-pacman.rst

      .. tab-item:: CentOS Stream
         :sync: centos-stream

         .. include:: git-dnf.rst

      .. tab-item:: Debian
         :sync: debian

         .. include:: git-apt.rst

      .. tab-item:: Fedora Linux
         :sync: fedora-linux

         .. include:: git-dnf.rst

      .. tab-item:: Linux Mint
         :sync: linux-mint

         .. include:: git-apt.rst

      .. tab-item:: OpenSUSE Leap
         :sync: opensuse-leap

         .. include:: git-zypper.rst

      .. tab-item:: OpenSUSE Tumbleweed
         :sync: opensuse-tumbleweed

         .. include:: git-zypper.rst

      .. tab-item:: Oracle Linux
         :sync: oracle-linux

         .. include:: git-dnf.rst

      .. tab-item:: RHEL
         :sync: rhel

         .. include:: git-dnf.rst

      .. tab-item:: Rocky Linux
         :sync: rocky-linux

         .. include:: git-dnf.rst

      .. tab-item:: Ubuntu
         :sync: ubuntu

         .. include:: git-apt.rst
