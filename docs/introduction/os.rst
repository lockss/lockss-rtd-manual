================
Operating System
================

The LOCKSS system requires a **64-bit Linux** host (physical or virtual) compatible with `K3s <https://k3s.io/>`_, a lightweight Kubernetes distribution by `Rancher <https://rancher.com/>`_.

Rancher states [#fn1]_ that "K3s is expected to work on most modern Linux systems", and that "Some OSs have specific requirements" (which are documented here and integrated into the :program:`lockss-installer` scripts).

Flavors of Linux we have successfully tested include:

*  `AlmaLinux <https://almalinux.org/>`_ 8.4, 8.3.

*  `Arch Linux <https://archlinux.org/>`_ (rolling release).

*  `CentOS <https://www.centos.org/>`_ 8.3, 8.2, 8.1, 8.0, 7.9, 7.8, 7.7, 7.6, 7.5, 7.4, 7.3.

*  `Debian <https://www.debian.org/>`_ 10.9, 10.8, 10.7, 10.6, 10.5, 10.4, 10.3, 10.2, 10.1, 10.0, 9.13, 9.12, 9.11, 9.9, 9.8, 9.7.

*  `Fedora <https://getfedora.org/>`_ 34, 33, 32, 31.

*  `Linux Mint <https://linuxmint.com/>`_ 20.0.

*  `OpenSUSE <https://www.opensuse.org/>`_ Leap 15.2, 15.1, 15.0.

*  `Oracle Linux <https://www.oracle.com/linux/>`_ 8.3.

*  `RHEL <https://www.redhat.com/>`_ 8.3.

*  `Rocky Linux <https://rockylinux.org/>`_ 8.3 RC1.

*  `Ubuntu <https://ubuntu.com/>`_ 21.04, 20.10, 20.04 LTS, 19.10, 19.04, 18.10, 18.04 LTS.

LOCKSS 2.0-alpha4 can probably be installed successfully on slightly different versions of the Linux flavors above, as well as other Linux flavors.

*FIXME what do we recommend?*

----

.. rubric:: Footnotes

.. [#fn1]

   Reference: https://rancher.com/docs/k3s/latest/en/installation/installation-requirements/#operating-systems
