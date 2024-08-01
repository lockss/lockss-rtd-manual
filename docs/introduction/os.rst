================
Operating System
================

The LOCKSS system requires a **64-bit Linux** host (physical or virtual) compatible with `K3s <https://k3s.io/>`_, a lightweight open source Kubernetes distribution by `SUSE <https://www.suse.com/>`_. The K3s documentation states that "K3s is expected to work on most modern Linux systems", and that "Some OSs have additional setup requirements" [#fnk3sos]_ (which are documented in this manual and integrated into the LOCKSS Installer). Compatibility information for various operating systems can be found below.

.. dropdown:: AlmaLinux OS
   :name: os-almalinux
   :icon: thumbsup
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `AlmaLinux OS <https://almalinux.org/>`_.

   AlmaLinux OS is suitable for a same-host migration from LOCKSS 1.x to LOCKSS 2.x [#fnsamehostmigration]_.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   AlmaLinux OS        9.4       2027-05-31     2032-05-31       :octicon:`thumbsup`
   AlmaLinux OS        9.3       2027-05-31     2032-05-31       :octicon:`thumbsup`
   AlmaLinux OS        9.2       2027-05-31     2032-05-31       :octicon:`thumbsup`
   AlmaLinux OS        9.1       2027-05-31     2032-05-31       :octicon:`thumbsup`
   AlmaLinux OS        9.0       2027-05-31     2032-05-31       :octicon:`thumbsup`
   AlmaLinux OS        8.10      2024-05-01     2029-03-01       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`

   AlmaLinux OS        8.9       2024-05-01     2029-03-01       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`

   AlmaLinux OS        8.8       2024-05-01     2029-03-01       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`

   AlmaLinux OS        8.7       2024-05-01     2029-03-01       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`

   AlmaLinux OS        8.6       2024-05-01     2029-03-01       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`

   AlmaLinux OS        8.5       2024-05-01     2029-03-01       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`

   AlmaLinux OS        8.4       2024-05-01     2029-03-01       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`

   AlmaLinux OS        8.3       2024-05-01     2029-03-01       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   =================== ========= ============== ================ =====

.. dropdown:: Arch Linux :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-arch-linux
   :icon: thumbsup
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Arch Linux <https://archlinux.org/>`_.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Arch Linux                    Rolling        Rolling          :octicon:`thumbsup`
   =================== ========= ============== ================ =====

.. dropdown:: CentOS Linux :bdg-danger-line:`end of life`
   :name: os-centos-linux
   :icon: thumbsdown
   :animate: fade-in-slide-down

   .. warning::

      `CentOS Linux <https://www.centos.org/centos-linux/>`_ is at end of life and is not suitable for use with LOCKSS 2.x.

   .. tip::

      If you are currently running LOCKSS 1.x on a CentOS Linux host and you are considering a :doc:`same-host migration to LOCKSS 2.x <lockss:migration/index>`, you must upgrade your host to a newer operating system in the RHEL 8 or 9 family first, such as :ref:`os-rocky-linux`, :ref:`os-almalinux`, :ref:`os-oracle-linux`, :ref:`os-rhel`, or :ref:`os-eurolinux`. See `OS Upgrades <https://github.com/lockss/community/wiki/OS-Upgrades>`_ in the LOCKSS Community Wiki for guidance.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   CentOS Linux        8.5       2021-12-31     2021-12-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        8.4       2021-12-31     2021-12-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        8.3       2021-12-31     2021-12-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        8.2       2021-12-31     2021-12-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        8.1       2021-12-31     2021-12-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        8.0       2021-12-31     2021-12-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        7.9       2020-08-06     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        7.8       2020-08-06     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        7.7       2020-08-06     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        7.6       2020-08-06     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        7.5       2020-08-06     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        7.4       2020-08-06     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        7.3       2020-08-06     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        7.2       2020-08-06     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        7.1       2020-08-06     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        7.0       2020-08-06     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        6.10      2017-05-10     2020-11-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        6.9       2017-05-10     2020-11-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        6.8       2017-05-10     2020-11-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        6.7       2017-05-10     2020-11-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        6.6       2017-05-10     2020-11-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        6.5       2017-05-10     2020-11-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        6.4       2017-05-10     2020-11-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        6.3       2017-05-10     2020-11-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        6.2       2017-05-10     2020-11-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        6.1       2017-05-10     2020-11-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        6.0       2017-05-10     2020-11-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        5.11      2014-01-31     2017-03-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        5.10      2014-01-31     2017-03-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        5.9       2014-01-31     2017-03-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        5.8       2014-01-31     2017-03-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        5.7       2014-01-31     2017-03-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        5.6       2014-01-31     2017-03-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        5.5       2014-01-31     2017-03-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        5.4       2014-01-31     2017-03-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        5.3       2014-01-31     2017-03-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        5.2       2014-01-31     2017-03-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        5.1       2014-01-31     2017-03-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   CentOS Linux        5.0       2014-01-31     2017-03-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   =================== ========= ============== ================ =====

.. dropdown:: CentOS Stream :bdg-info-line:`not recommended`
   :name: os-centos-stream
   :icon: thumbsdown
   :animate: fade-in-slide-down

   .. warning::

      CentOS Stream 8 is at end of life and is not suitable for use with LOCKSS 2.x.

   .. tip::

      If you are currently running LOCKSS 1.x on a CentOS Stream 8 host and you are considering a :doc:`same-host migration to LOCKSS 2.x <lockss:migration/index>`, you must upgrade your host to a newer operating system in the RHEL 8 or 9 family first, such as :ref:`os-rocky-linux`, :ref:`os-almalinux`, :ref:`os-oracle-linux`, :ref:`os-rhel`, or :ref:`os-eurolinux`. See `OS Upgrades <https://github.com/lockss/community/wiki/OS-Upgrades>`_ in the LOCKSS Community Wiki for guidance.

   LOCKSS 2.x is compatible with `CentOS Stream <https://centos.org/centos-stream/>`_ 9, which is suitable for a same-host migration from LOCKSS 1.x to LOCKSS 2.x [#fnsamehostmigration]_, but we do not recommend CentOS Stream.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   CentOS Stream       9         2027-05-31     2027-05-31       :octicon:`thumbsdown` :bdg-info-line:`not recommended`
   CentOS Stream       8         2024-05-31     2024-05-31       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   =================== ========= ============== ================ =====

.. dropdown:: Debian :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-debian
   :icon: thumbsup
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Debian <https://www.debian.org/>`_.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Debian              12.6      2026-06-10     2028-06-10       :octicon:`thumbsup`
   Debian              12.5      2026-06-10     2028-06-10       :octicon:`thumbsup`
   Debian              12.4      2026-06-10     2028-06-10       :octicon:`thumbsup`
   Debian              12.3      2026-06-10     2028-06-10       :octicon:`thumbsup`
   Debian              12.2      2026-06-10     2028-06-10       :octicon:`thumbsup`
   Debian              12.1      2026-06-10     2028-06-10       :octicon:`thumbsup`
   Debian              12.0      2026-06-10     2028-06-10       :octicon:`thumbsup`
   Debian              11.10     2024-07-01     2026-08-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Debian              11.9      2024-07-01     2026-08-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Debian              11.8      2024-07-14     2026-08-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Debian              11.7      2024-07-14     2026-08-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Debian              11.6      2024-07-14     2026-08-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Debian              11.5      2024-07-14     2026-08-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Debian              11.4      2024-07-14     2026-08-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Debian              11.3      2024-07-14     2026-08-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Debian              11.2      2024-07-14     2026-08-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Debian              11.1      2024-07-14     2026-08-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Debian              11.0      2024-07-14     2026-08-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   =================== ========= ============== ================ =====

.. dropdown:: EuroLinux
   :name: os-eurolinux
   :icon: thumbsup
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `EuroLinux <https://en.euro-linux.com/eurolinux>`_.

   EuroLinux is suitable for a same-host migration from LOCKSS 1.x to LOCKSS 2.x [#fnsamehostmigration]_.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   EuroLinux           9.4       2032-05-31     2032-06-30       :octicon:`thumbsup`
   EuroLinux           9.3       2032-05-31     2032-06-30       :octicon:`thumbsup`
   EuroLinux           9.2       2032-05-31     2032-06-30       :octicon:`thumbsup`
   EuroLinux           9.1       2032-05-31     2032-06-30       :octicon:`thumbsup`
   EuroLinux           9.0       2032-05-31     2032-06-30       :octicon:`thumbsup`
   EuroLinux           8.10      2029-03-01     2029-06-30       :octicon:`thumbsup`
   EuroLinux           8.9       2029-03-01     2029-06-30       :octicon:`thumbsup`
   EuroLinux           8.8       2029-03-01     2029-06-30       :octicon:`thumbsup`
   EuroLinux           8.7       2029-03-01     2029-06-30       :octicon:`thumbsup`
   EuroLinux           8.6       2029-03-01     2029-06-30       :octicon:`thumbsup`
   EuroLinux           8.5       2029-03-01     2029-06-30       :octicon:`thumbsup`
   EuroLinux           8.4       2029-03-01     2029-06-30       :octicon:`thumbsup`
   EuroLinux           8.3       2029-03-01     2029-06-30       :octicon:`thumbsup`
   EuroLinux           8.2       2029-03-01     2029-06-30       :octicon:`thumbsup`
   EuroLinux           8.1       2029-03-01     2029-06-30       :octicon:`thumbsup`
   EuroLinux           8.0       2029-03-01     2029-06-30       :octicon:`thumbsup`
   =================== ========= ============== ================ =====

.. dropdown:: Fedora Linux :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-fedora-linux
   :icon: thumbsup
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Fedora Linux <https://getfedora.org/>`_.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Fedora Linux        40        2025-05-13     2025-05-13       :octicon:`thumbsup`
   Fedora Linux        39        2024-11-12     2024-11-12       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   =================== ========= ============== ================ =====

.. dropdown:: Linux Mint :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-linux-mint
   :icon: thumbsup
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Linux Mint <https://linuxmint.com/>`_.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Linux Mint          22        Yes            2029-04-30       :octicon:`thumbsup`
   Linux Mint          21.3      Yes            2027-04-30       :octicon:`thumbsup`
   Linux Mint          21.2      Yes            2027-04-30       :octicon:`thumbsup`
   Linux Mint          21.1      Yes            2027-04-30       :octicon:`thumbsup`
   Linux Mint          21        Yes            2027-04-30       :octicon:`thumbsup`
   Linux Mint          20.3      Yes            2025-04-25       :octicon:`thumbsup`
   Linux Mint          20.2      Yes            2025-04-25       :octicon:`thumbsup`
   Linux Mint          20.1      No             2025-04-25       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Linux Mint          20        No             2025-04-25       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   =================== ========= ============== ================ =====

.. dropdown:: OpenSUSE :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-opensuse
   :icon: thumbsup
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `OpenSUSE <https://www.opensuse.org/>`_.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   OpenSUSE Tumbleweed           Rolling        Rolling          :octicon:`thumbsup`
   OpenSUSE Leap       15.6      2025-12-31     2025-12-31       :octicon:`thumbsup`
   OpenSUSE Leap       15.5      2024-12-31     2024-12-31       :octicon:`thumbsup`
   =================== ========= ============== ================ =====

.. dropdown:: Oracle Linux
   :name: os-oracle-linux
   :icon: thumbsup
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Oracle Linux <https://www.oracle.com/linux>`_.

   Oracle Linux is suitable for a same-host migration from LOCKSS 1.x to LOCKSS 2.x [#fnsamehostmigration]_.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Oracle Linux        9.4       2032-06-30     2035-06-30       :octicon:`thumbsup`
   Oracle Linux        9.3       2032-06-30     2035-06-30       :octicon:`thumbsup`
   Oracle Linux        9.2       2032-06-30     2035-06-30       :octicon:`thumbsup`
   Oracle Linux        9.1       2032-06-30     2035-06-30       :octicon:`thumbsup`
   Oracle Linux        9.0       2032-06-30     2035-06-30       :octicon:`thumbsup`
   Oracle Linux        8.10      2029-07-31     2032-07-31       :octicon:`thumbsup`
   Oracle Linux        8.9       2029-07-31     2032-07-31       :octicon:`thumbsup`
   Oracle Linux        8.8       2029-07-31     2032-07-31       :octicon:`thumbsup`
   Oracle Linux        8.7       2029-07-31     2032-07-31       :octicon:`thumbsup`
   Oracle Linux        8.6       2029-07-31     2032-07-31       :octicon:`thumbsup`
   Oracle Linux        8.5       2029-07-31     2032-07-31       :octicon:`thumbsup`
   Oracle Linux        8.4       2029-07-31     2032-07-31       :octicon:`thumbsup`
   Oracle Linux        8.3       2029-07-31     2032-07-31       :octicon:`thumbsup`
   Oracle Linux        8.2       2029-07-31     2032-07-31       :octicon:`thumbsup`
   Oracle Linux        8.1       2029-07-31     2032-07-31       :octicon:`thumbsup`
   Oracle Linux        8.0       2029-07-31     2032-07-31       :octicon:`thumbsup`
   Oracle Linux        7.9       2024-12-31     2028-06-30       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Oracle Linux        7.8       2024-07-01     2028-06-30       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Oracle Linux        7.7       2024-07-01     2028-06-30       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Oracle Linux        7.6       2024-07-01     2028-06-30       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Oracle Linux        7.5       2024-07-01     2028-06-30       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Oracle Linux        7.4       2024-07-01     2028-06-30       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Oracle Linux        7.3       2024-07-01     2028-06-30       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Oracle Linux        7.2       2024-07-01     2028-06-30       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Oracle Linux        7.1       2024-07-01     2028-06-30       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Oracle Linux        7.0       2024-07-01     2028-06-30       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   =================== ========= ============== ================ =====

.. dropdown:: Red Hat Enterprise Linux (RHEL)
   :name: os-rhel
   :icon: thumbsup
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `RHEL <https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux>`_.

   RHEL is suitable for a same-host migration from LOCKSS 1.x to LOCKSS 2.x [#fnsamehostmigration]_.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   RHEL                9.4       2027-05-31     2032-05-31       :octicon:`thumbsup`
   RHEL                9.3       2027-05-31     2032-05-31       :octicon:`thumbsup`
   RHEL                9.2       2027-05-31     2032-05-31       :octicon:`thumbsup`
   RHEL                9.1       2027-05-31     2032-05-31       :octicon:`thumbsup`
   RHEL                9.0       2027-05-31     2032-05-31       :octicon:`thumbsup`
   RHEL                8.10      2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   RHEL                8.9       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   RHEL                8.8       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   RHEL                8.7       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   RHEL                8.6       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   RHEL                8.5       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   RHEL                8.4       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   RHEL                8.3       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   RHEL                8.2       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   RHEL                8.1       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   RHEL                8.0       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   =================== ========= ============== ================ =====

.. dropdown:: Rocky Linux
   :name: os-rocky-linux
   :icon: thumbsup
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Rocky Linux <https://rockylinux.org/>`_.

   Rocky Linux is suitable for a same-host migration from LOCKSS 1.x to LOCKSS 2.x [#fnsamehostmigration]_.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Rocky Linux         9.4       2027-05-31     2032-05-31       :octicon:`thumbsup`
   Rocky Linux         9.3       2027-05-31     2032-05-31       :octicon:`thumbsup`
   Rocky Linux         9.2       2027-05-31     2032-05-31       :octicon:`thumbsup`
   Rocky Linux         9.1       2027-05-31     2032-05-31       :octicon:`thumbsup`
   Rocky Linux         9.0       2027-05-31     2032-05-31       :octicon:`thumbsup`
   Rocky Linux         8.10      2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Rocky Linux         8.9       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Rocky Linux         8.8       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Rocky Linux         8.7       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Rocky Linux         8.6       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Rocky Linux         8.5       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Rocky Linux         8.4       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   Rocky Linux         8.3       2024-05-31     2029-05-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   =================== ========= ============== ================ =====

.. dropdown:: Scientific Linux :bdg-danger-line:`end of life`
   :name: os-scientific-linux
   :icon: thumbsdown
   :animate: fade-in-slide-down

   .. warning::

      `Scientific Linux <https://scientificlinux.org/>`_ is at end of life and is not suitable for use with LOCKSS 2.x.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Scientific Linux    7.9       2024-06-30     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Scientific Linux    7.8       2024-06-30     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Scientific Linux    7.7       2024-06-30     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Scientific Linux    7.6       2024-06-30     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Scientific Linux    7.5       2024-06-30     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Scientific Linux    7.4       2024-06-30     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Scientific Linux    7.3       2024-06-30     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Scientific Linux    7.2       2024-06-30     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Scientific Linux    7.1       2024-06-30     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Scientific Linux    7.0       2024-06-30     2024-06-30       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   =================== ========= ============== ================ =====

.. dropdown:: SUSE Linux Enterprise Server (SLES) :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-sles
   :icon: thumbsup
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `SLES <https://www.suse.com/products/server/>`_.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   SLES                15.6      Yes            Yes              :octicon:`thumbsup`
   SLES                15.5      2024-12-31     2027-12-31       :octicon:`thumbsup`
   SLES                15.4      2023-12-31     2026-12-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   SLES                15.3      2022-12-31     2025-12-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   SLES                15.2      2021-12-31     2024-12-31       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   =================== ========= ============== ================ =====

.. dropdown:: Ubuntu :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-ubuntu
   :icon: thumbsup
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Ubuntu <https://ubuntu.com/>`_.

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Ubuntu              24.04 LTS 2029-04-25     2029-04-25       :octicon:`thumbsup`
   Ubuntu              23.10     2024-07-11     2024-07-11       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Ubuntu              23.04     2024-01-20     2024-01-20       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Ubuntu              22.10     2023-07-29     2023-07-29       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Ubuntu              22.04 LTS 2024-09-20     2027-04-01       :octicon:`thumbsup`
   Ubuntu              21.10     2022-07-14     2022-07-14       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Ubuntu              21.04     2022-01-20     2022-01-20       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Ubuntu              20.10     2021-07-22     2021-07-22       :octicon:`x-circle-fill` :bdg-danger:`end of life`
   Ubuntu              20.04 LTS 2022-10-01     2025-04-02       :octicon:`thumbsup` :bdg-warning-line:`obsolescent`
   =================== ========= ============== ================ =====

The LOCKSS system can likely be installed successfully on additional flavors of  Linux. We welcome reports of successful installations from the community so they can be added to the list above.

.. tip::

   If your IT environment does not favor a particular flavor of Linux, we recommend :ref:`os-rocky-linux`, both for brand-new installations and for :doc:`either new-host or same-host migrations from LOCKSS 1.x <lockss:migration/index>`.

----

.. rubric:: Footnotes

.. [#fnk3sos]

   Reference: https://docs.k3s.io/installation/requirements#operating-systems

.. [#fnsamehostmigration]

   Reference: :doc:`lockss:migration/index`
