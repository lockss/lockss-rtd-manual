====================
System Prerequisites
====================

-------
Machine
-------

The LOCKSS system runs on a **64-bit Linux** host (physical or virtual), with **4 cores** (8 or more preferable) and **8 GB of memory** (16 GB or more preferable).

----------------
Operating System
----------------

The LOCKSS system requires a **64-bit Linux** host compatible with `Systemd <https://www.freedesktop.org/wiki/Software/systemd/>`_ and `Docker <https://www.docker.com/>`_ **18.09 or better**.

Many Linux distributions have systemd and can run Docker 18.09 or better. To name a few that are commonly used with the LOCKSS system:

*  `Arch Linux <https://www.archlinux.org/>`_
*  `CentOS <https://www.centos.org/>`_ 7
*  `Debian <https://www.debian.org/>`_ 9 (Stretch)
*  `Fedora <https://getfedora.org/>`_ 28 or better
*  `Oracle Linux <https://www.oracle.com/linux/>`_ 7
*  `Ubuntu <https://www.ubuntu.com/>`_ 16.04 LTS (Xenial) or better

----
User
----

The LOCKSS system runs under a system user named ``lockss`` under a group named ``lockss``, which you will need to create. **For alpha2 only, the lockss user must have sudo privileges.**

To check installed prerequisites, use the script :doc:`check-sys <check-sys>`, which will attempt to find and install missing elements.
