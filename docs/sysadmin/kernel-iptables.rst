===================================================
Installing the ``ip_tables`` Loadable Kernel Module
===================================================

:term:`K3s`, the :term:`Kubernetes` distribution used by |LOCKSS| uses its own embedded :term:`iptables` program, but this in turn requires the ``ip_tables`` loadable kernel module, even if :term:`iptables` or :term:`nftables` is not installed on the host system. Most versions of the :ref:`Compatible Operating Systems` satisfy this requirement out of the box. This section describes how to install the ``ip_tables`` loadable kernel module on some operating systems.

.. include:: kernel-iptables-tip.rst

.. include:: kernel-iptables-test.rst

If installing the ``ip_tables`` loadable kernel module is required, select your operating system below, and if applicable select the particular version of your operating system, then follow the instructions accordingly:

.. COMMENT OSTABS

.. tab-set::

   .. tab-item:: AlmaLinux OS
      :sync: almalinux-os

      .. tab-set::

         .. tab-item:: AlmaLinux OS 8
            :sync: almalinux-os-8

            .. include:: kernel-iptables-none.rst

         .. tab-item:: AlmaLinux OS 9
            :sync: almalinux-os-9

            .. include:: kernel-iptables-none.rst

         .. tab-item:: AlmaLinux OS 10
            :sync: almalinux-os-10

            .. include:: kernel-iptables-dnf.rst

   .. tab-item:: Arch Linux
      :sync: arch-linux

      .. include:: kernel-iptables-none.rst

   .. tab-item:: CentOS Stream
      :sync: centos-stream

      .. include:: kernel-iptables-none.rst

   .. tab-item:: Debian
      :sync: debian

      .. include:: kernel-iptables-none.rst

   .. tab-item:: Fedora Linux
      :sync: fedora-linux

      .. include:: kernel-iptables-none.rst

   .. tab-item:: Linux Mint
      :sync: linux-mint

      .. include:: kernel-iptables-none.rst

   .. tab-item:: OpenSUSE Leap
      :sync: opensuse-leap

      .. include:: kernel-iptables-none.rst

   .. tab-item:: OpenSUSE Tumbleweed
      :sync: opensuse-tumbleweed

      .. include:: kernel-iptables-none.rst

   .. tab-item:: Oracle Linux
      :sync: oracle-linux

      .. tab-set::

         .. tab-item:: Oracle Linux 8
            :sync: oracle-linux-8

            .. include:: kernel-iptables-none.rst

         .. tab-item:: Oracle Linux 9
            :sync: oracle-linux-9

            .. include:: kernel-iptables-none.rst

         .. tab-item:: Oracle Linux 10
            :sync: oracle-linux-10

            .. include:: kernel-iptables-dnf.rst

   .. tab-item:: Red Hat Enterprise Linux
      :sync: rhel

      .. tab-set::

         .. tab-item:: Red Hat Enterprise Linux 8
            :sync: rhel-8

            .. include:: kernel-iptables-none.rst

         .. tab-item:: Red Hat Enterprise Linux 9
            :sync: rhel-9

            .. include:: kernel-iptables-none.rst

         .. tab-item:: Red Hat Enterprise Linux 10
            :sync: rhel-10

            .. include:: kernel-iptables-dnf.rst

   .. tab-item:: Rocky Linux
      :sync: rocky-linux

      .. tab-set::

         .. tab-item:: Rocky Linux 8
            :sync: rocky-linux-8

            .. include:: kernel-iptables-none.rst

         .. tab-item:: Rocky Linux 9
            :sync: rocky-linux-9

            .. include:: kernel-iptables-none.rst

         .. tab-item:: Rocky Linux 10
            :sync: rocky-linux-10

            .. include:: kernel-iptables-dnf.rst

   .. tab-item:: SUSE Linux Enterprise Server
      :sync: sles

      .. include:: kernel-iptables-none.rst

   .. tab-item:: Ubuntu
      :sync: ubuntu

      .. include:: kernel-iptables-none.rst
