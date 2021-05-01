====================
System Prerequisites
====================

-------
Machine
-------

The LOCKSS system runs on a **64-bit Linux host** (physical or virtual), with at least **4 cores** (8 or more preferable), at least **8 GB of memory** (16 GB or more preferable), and at least **50 GB of disk space** (100 GB or more preferable; considerably more depending on the amount of content to be preserved).

----------------
Operating System
----------------

The LOCKSS system requires a **64-bit Linux** host compatible with `K3s <https://k3s.io/>`_, a lightweight Kubernetes distribution by `Rancher <https://rancher.com/>`_. Rancher states [#f1]_ that "K3s is expected to work on most modern Linux systems", and that "Some OSs have specific requirements" (which are documented here and integrated into the :program:`lockss-installer` scripts).

Flavors of Linux we have successfully tested include:

*  `Arch Linux <https://archlinux.org/>`_ (rolling release).

*  `CentOS <https://www.centos.org/>`_ 7.9.

*  `Debian <https://www.debian.org/>`_ 10.8.

*  `Fedora <https://getfedora.org/>`_ 33.

*  `Linux Mint <https://linuxmint.com/>`_ 20.0.

*  `OpenSUSE <https://www.opensuse.org/>`_ Leap 15.2.

*  `Oracle Linux <https://www.oracle.com/linux/>`_ 8.3.

*  `RHEL <https://www.redhat.com/>`_ 8.3.

*  `Ubuntu <https://ubuntu.com/>`_ 21.04, 20.10.

LOCKSS 2.0-alpha4 can probably be installed successfully on slightly different versions of the Linux flavors above, as well as other Linux flavors.

----

.. rubric:: Footnotes

.. [#f1]

   Reference: https://rancher.com/docs/k3s/latest/en/installation/installation-requirements/#operating-systems
