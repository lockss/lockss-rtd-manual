================
Operating System
================

The LOCKSS system requires a **64-bit Linux** host (physical or virtual) compatible with `K3s <https://k3s.io/>`_, a lightweight Kubernetes distribution by `Rancher <https://rancher.com/>`_. The K3s documentation states [#fnk3sos]_ that "K3s is expected to work on most modern Linux systems", and that "Some OSs have specific requirements" (which are documented in this manual and integrated into the :program:`lockss-installer` scripts).

The LOCKSS team has successfully tested the LOCKSS system installation process on many flavors of Linux, some of which are listed below:

.. COMMENT OSTABS

.. tab-set::
   :class: sd-bg-light

   .. tab-item:: AlmaLinux
      :sync: alma

      The LOCKSS system is compatible with `AlmaLinux <https://almalinux.org/>`_ 8.4, 8.3.

   .. tab-item:: Arch Linux
      :sync: arch

      The LOCKSS system is compatible with `Arch Linux <https://archlinux.org/>`_ :bdg-info:`rolling release`.

   .. tab-item:: CentOS
      :sync: centos

      The LOCKSS system is compatible with different flavors of `CentOS <https://centos.org>`_:

      .. tab-set::

         .. tab-item:: CentOS Stream
            :sync: centosstream

            The LOCKSS system is compatible with `CentOS Stream <https://centos.org/centos-stream/>`_ :bdg-info:`rolling release`.

         .. tab-item:: CentOS Linux 7
            :sync: centos7


            The LOCKSS system is compatible with `CentOS Linux <https://centos.org/centos-linux/>`_ 7.9, 7.8, 7.7, 7.6, 7.5, 7.4, 7.3.

            .. warning::

               The end-of-life date for CentOS Linux 7 is 2024-06-30.

   .. tab-item:: Debian
      :sync: debian

      The LOCKSS system is compatible with `Debian <https://www.debian.org/>`_ 11.1, 11.0, 10.10, 10.9, 10.8, 10.7, 10.6, 10.5, 10.4, 10.3, 10.2, 10.1, 10.0.

         .. warning::

            The end-of-life date for Debian 10 (Buster) is June 2024.

   .. tab-item:: EuroLinux
      :sync: eurolinux

      The LOCKSS system is compatible with different flavors of `EuroLinux <https://en.euro-linux.com/eurolinux>`_:

      .. tab-set::

         .. tab-item:: EuroLinux 8-9
            :sync: eurolinux8

            The LOCKSS system is compatible with `EuroLinux <https://en.euro-linux.com/eurolinux>`_ 8.4, 8.3.

         .. tab-item:: EuroLinux 7
            :sync: eurolinux7

            The LOCKSS system is compatible with `EuroLinux <https://en.euro-linux.com/eurolinux>`_ 8.4, 8.3, 7.9, 7.8, 7.7, 7.6.

            .. warning::

               The end-of-life date for EuroLinux 7 is 2024-06-30.

   .. tab-item:: Fedora Linux
      :sync: fedora

      The LOCKSS system is compatible with `Fedora Linux <https://getfedora.org/>`_ 34.

      .. warning::

         The end-of-life date for Fedora Linux 34 was 2022-06-07.

   .. tab-item:: Linux Mint
      :sync: mint

      The LOCKSS system is compatible with `Linux Mint <https://linuxmint.com/>`_ 20.2, 20.1, 20.0, 19.3, 19.2, 19.1, 19.0.

      .. caution::

          The end-of-life date for Linux Mint 19 is April 2023.

   .. tab-item:: OpenSUSE
      :sync: opensuse

      The LOCKSS system is compatible with different flavors of `OpenSUSE <https://www.opensuse.org/>`_:

      .. tab-set::

         .. tab-item:: OpenSUSE Tumbleweed
            :sync: opensusetumbleweed

            The LOCKSS system is compatible with `OpenSUSE Tumbleweed <https://get.opensuse.org/tumbleweed>`_ :bdg-info:`rolling release`.

         .. tab-item:: OpenSUSE Leap
            :sync: opensuseleap

            The LOCKSS system is compatible with `OpenSUSE Leap <https://get.opensuse.org/leap>`_ Leap 15.3.

   .. tab-item:: Oracle Linux
      :sync: oracle

      The LOCKSS system is compatible with different flavors of `Oracle Linux <https://www.oracle.com/linux>`_:

      .. tab-set::

         .. tab-item:: Oracle Linux 8-9
            :sync: oracle8

            The LOCKSS system is compatible with `Oracle Linux <https://www.oracle.com/linux/>`_ 8.4, 8.3, 8.2, 8.1.

         .. tab-item:: Oracle Linux 7
            :sync: oracle7

            The LOCKSS system is compatible with `Oracle Linux <https://www.oracle.com/linux/>`_ 7.9, 7.8, 7.7, 7.6.

   .. tab-item:: RHEL
      :sync: rhel

      The LOCKSS system is compatible with different flavors of `RHEL <https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux>`_:

      .. tab-set::

         .. tab-item:: RHEL 8-9
            :sync: rhel8

            The LOCKSS system is compatible with `RHEL <https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux>`_ 8.3.

         .. tab-item:: RHEL 7
            :sync: rhel7

            The LOCKSS system is compatible with RHEL 7.

            .. warning::

                The end-of-life date for RHEL 7 is 2024-06-30.

   .. tab-item:: Rocky Linux
      :sync: rocky

      The LOCKSS system is compatible with `Rocky Linux <https://rockylinux.org/>`_ 8.4.

   .. tab-item:: Scientific Linux
      :sync: scientific

      The LOCKSS system is compatible with `Scientific Linux <https://scientificlinux.org/>`_ 7.9, 7.8, 7.7, 7.6.

      .. warning::

          The end-of-life date for Scientific Linux 7 is 2024-06-30.

   .. tab-item:: Ubuntu
      :sync: ubuntu

      The LOCKSS system is compatible with `Ubuntu <https://ubuntu.com/>`_ 21.10, 21.04, 20.10, 20.04 :bdg-success:`LTS`, 18.04 :bdg-success:`LTS`.

.. COMMENT the pipe below is to force some vertical space, otherwise it's too cramped

|

The LOCKSS system can likely be installed successfully on slightly different versions of the Linux flavors above, as well as other Linux flavors altogether.

.. tip::

   We currently recommend `Rocky Linux <https://rockylinux.org/>`_.

----

.. rubric:: Footnotes

.. [#fnk3sos]

   Reference: https://docs.k3s.io/installation/requirements#operating-systems
