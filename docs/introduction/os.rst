================
Operating System
================

:Section last updated: 2025-12-19

The LOCKSS system requires a **64-bit Linux** host (physical or virtual) compatible with `K3s <https://k3s.io/>`_, a lightweight open source Kubernetes distribution by `SUSE <https://www.suse.com/>`_ (formerly by Rancher). The K3s documentation states that "K3s is expected to work on most modern Linux systems", and that "Some OSs have additional setup requirements" [#fn-k3s-os]_ (which are documented in this manual and integrated into the LOCKSS Installer). Compatibility information for various operating systems can be found in this section.

----------------------------
Compatible Operating Systems
----------------------------

LOCKSS 2.x is compatible with the following operating systems. Note that the LOCKSS system can likely be installed successfully on additional flavors of Linux; we welcome reports of successful installations from the community so they can be added to the list below.

.. tip::

   If your IT environment does not favor a particular flavor of Linux, we recommend :ref:`os-rocky-linux`, both for brand-new installations and for :doc:`either new-host or same-host migrations from LOCKSS 1.x <lockss-portal:migration/index>`.

.. dropdown:: AlmaLinux OS
   :name: os-almalinux
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `AlmaLinux OS <https://almalinux.org/>`_.

   AlmaLinux OS is suitable for a same-host migration from LOCKSS 1.x to LOCKSS 2.x [#fnsamehostmigration]_.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  AlmaLinux OS
         *  10.1
         *  2030-05-31
         *  2035-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel-iptables]_
      *  *  AlmaLinux OS
         *  10.0
         *  2030-05-31
         *  2035-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel-iptables]_
      *  *  AlmaLinux OS
         *  9.6
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  AlmaLinux OS
         *  9.5
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  AlmaLinux OS
         *  9.4
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  AlmaLinux OS
         *  9.3
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  AlmaLinux OS
         *  9.2
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  AlmaLinux OS
         *  9.1
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  AlmaLinux OS
         *  9.0
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  AlmaLinux OS
         *  8.10
         *  :octicon:`alert-fill` 2024-05-01
         *  2029-03-01
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  AlmaLinux OS
         *  8.9
         *  :octicon:`alert-fill` 2024-05-01
         *  2029-03-01
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  AlmaLinux OS
         *  8.8
         *  :octicon:`alert-fill` 2024-05-01
         *  2029-03-01
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  AlmaLinux OS
         *  8.7
         *  :octicon:`alert-fill` 2024-05-01
         *  2029-03-01
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  AlmaLinux OS
         *  8.6
         *  :octicon:`alert-fill` 2024-05-01
         *  2029-03-01
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  AlmaLinux OS
         *  8.5
         *  :octicon:`alert-fill` 2024-05-01
         *  2029-03-01
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  AlmaLinux OS
         *  8.4
         *  :octicon:`alert-fill` 2024-05-01
         *  2029-03-01
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  AlmaLinux OS
         *  8.3
         *  :octicon:`alert-fill` 2024-05-01
         *  2029-03-01
         *  :bdg-info-line:`footnote` [#fn-kernel54]_

.. dropdown:: Arch Linux :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-arch-linux
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Arch Linux <https://archlinux.org/>`_.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  Arch Linux
         *  Rolling
         *  Rolling
         *  Rolling
         *  

.. dropdown:: CentOS Stream
   :name: os-centos-stream
   :animate: fade-in-slide-down

   .. caution::

      CentOS Stream, which is suitable for use with LOCKSS 2.x, should not be confused with :ref:`CentOS Linux <os-centos-linux>`, which is at end of life and is **not** suitable for use with LOCKSS 2.x.

   LOCKSS 2.x is compatible with `CentOS Stream <https://centos.org/centos-stream/>`_.

   CentOS Stream is suitable for a same-host migration from LOCKSS 1.x to LOCKSS 2.x [#fnsamehostmigration]_.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  CentOS Stream
         *  10
         *  2030-01-01
         *  2030-01-01
         *  
      *  *  CentOS Stream
         *  9
         *  2027-05-31
         *  2027-05-31
         *  

.. dropdown:: Debian :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-debian
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Debian <https://www.debian.org/>`_.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  Debian
         *  13.3
         *  2028-08-09
         *  2030-06-30
         *  
      *  *  Debian
         *  13.2
         *  2028-08-09
         *  2030-06-30
         *  
      *  *  Debian
         *  13.2
         *  2028-08-09
         *  2030-06-30
         *  
      *  *  Debian
         *  13.1
         *  2028-08-09
         *  2030-06-30
         *  
      *  *  Debian
         *  13.0
         *  2028-08-09
         *  2030-06-30
         *  
      *  *  Debian
         *  12.12
         *  2026-06-10
         *  2028-06-30
         *  
      *  *  Debian
         *  12.11
         *  2026-06-10
         *  2028-06-30
         *  
      *  *  Debian
         *  12.10
         *  2026-06-10
         *  2028-06-30
         *  
      *  *  Debian
         *  12.9
         *  2026-06-10
         *  2028-06-30
         *  
      *  *  Debian
         *  12.8
         *  2026-06-10
         *  2028-06-30
         *  
      *  *  Debian
         *  12.7
         *  2026-06-10
         *  2028-06-30
         *  
      *  *  Debian
         *  12.6
         *  2026-06-10
         *  2028-06-30
         *  
      *  *  Debian
         *  12.5
         *  2026-06-10
         *  2028-06-30
         *  
      *  *  Debian
         *  12.4
         *  2026-06-10
         *  2028-06-30
         *  
      *  *  Debian
         *  12.3
         *  2026-06-10
         *  2028-06-30
         *  
      *  *  Debian
         *  12.2
         *  2026-06-10
         *  2028-06-30
         *  
      *  *  Debian
         *  12.1
         *  2026-06-10
         *  2028-06-30
         *  
      *  *  Debian
         *  12.0
         *  2026-06-10
         *  2028-06-30
         *  
      *  *  Debian
         *  11.11
         *  :octicon:`alert-fill` 2024-08-14
         *  2026-08-31
         *  
      *  *  Debian
         *  11.10
         *  :octicon:`alert-fill` 2024-08-14
         *  2026-08-31
         *  
      *  *  Debian
         *  11.9
         *  :octicon:`alert-fill` 2024-08-14
         *  2026-08-31
         *  
      *  *  Debian
         *  11.8
         *  :octicon:`alert-fill` 2024-08-14
         *  2026-08-31
         *  
      *  *  Debian
         *  11.7
         *  :octicon:`alert-fill` 2024-08-14
         *  2026-08-31
         *  
      *  *  Debian
         *  11.6
         *  :octicon:`alert-fill` 2024-08-14
         *  2026-08-31
         *  
      *  *  Debian
         *  11.5
         *  :octicon:`alert-fill` 2024-08-14
         *  2026-08-31
         *  
      *  *  Debian
         *  11.4
         *  :octicon:`alert-fill` 2024-08-14
         *  2026-08-31
         *  
      *  *  Debian
         *  11.3
         *  :octicon:`alert-fill` 2024-08-14
         *  2026-08-31
         *  
      *  *  Debian
         *  11.2
         *  :octicon:`alert-fill` 2024-08-14
         *  2026-08-31
         *  
      *  *  Debian
         *  11.1
         *  :octicon:`alert-fill` 2024-08-14
         *  2026-08-31
         *  
      *  *  Debian
         *  11.0
         *  :octicon:`alert-fill` 2024-08-14
         *  2026-08-31
         *  

.. dropdown:: Fedora Linux :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-fedora-linux
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Fedora Linux <https://getfedora.org/>`_.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  Fedora Linux
         *  43
         *  2026-12-09
         *  2026-12-09
         *  
      *  *  Fedora Linux
         *  42
         *  2026-05-13
         *  2026-05-13
         *  

.. dropdown:: Linux Mint :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-linux-mint
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Linux Mint <https://linuxmint.com/>`_.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  Linux Mint
         *  22.3
         *  Yes
         *  2029-04-30
         *  
      *  *  Linux Mint
         *  22.2
         *  Yes
         *  2029-04-30
         *  
      *  *  Linux Mint
         *  22.1
         *  Yes
         *  2029-04-30
         *  
      *  *  Linux Mint
         *  22
         *  Yes
         *  2029-04-30
         *  
      *  *  Linux Mint
         *  21.3
         *  Yes
         *  2027-04-30
         *  
      *  *  Linux Mint
         *  21.2
         *  Yes
         *  2027-04-30
         *  
      *  *  Linux Mint
         *  21.1
         *  Yes
         *  2027-04-30
         *  
      *  *  Linux Mint
         *  21
         *  Yes
         *  2027-04-30
         *  

.. dropdown:: OpenSUSE :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-opensuse
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `OpenSUSE <https://www.opensuse.org/>`_.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  OpenSUSE Tumbleweed
         *  Rolling
         *  Rolling
         *  Rolling
         *  
      *  *  OpenSUSE Leap
         *  16.0
         *  2027-10-31
         *  2027-10-31
         *  
      *  *  OpenSUSE Leap
         *  15.6
         *  2026-04-04
         *  2026-04-04
         *  

.. dropdown:: Oracle Linux
   :name: os-oracle-linux
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Oracle Linux <https://www.oracle.com/linux>`_.

   Oracle Linux is suitable for a same-host migration from LOCKSS 1.x to LOCKSS 2.x [#fnsamehostmigration]_.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  Oracle Linux
         *  10.1
         *  Yes
         *  Yes
         *  :bdg-info-line:`footnote` [#fn-kernel-iptables]_
      *  *  Oracle Linux
         *  10.0
         *  Yes
         *  Yes
         *  :bdg-info-line:`footnote` [#fn-kernel-iptables]_
      *  *  Oracle Linux
         *  9.6
         *  2032-06-30
         *  2035-06-30
         *  
      *  *  Oracle Linux
         *  9.5
         *  2032-06-30
         *  2035-06-30
         *  
      *  *  Oracle Linux
         *  9.4
         *  2032-06-30
         *  2035-06-30
         *  
      *  *  Oracle Linux
         *  9.3
         *  2032-06-30
         *  2035-06-30
         *  
      *  *  Oracle Linux
         *  9.2
         *  2032-06-30
         *  2035-06-30
         *  
      *  *  Oracle Linux
         *  9.1
         *  2032-06-30
         *  2035-06-30
         *  
      *  *  Oracle Linux
         *  9.0
         *  2032-06-30
         *  2035-06-30
         *  
      *  *  Oracle Linux
         *  8.10
         *  2029-07-31
         *  2032-07-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Oracle Linux
         *  8.9
         *  2029-07-31
         *  2032-07-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Oracle Linux
         *  8.8
         *  2029-07-31
         *  2032-07-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Oracle Linux
         *  8.7
         *  2029-07-31
         *  2032-07-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Oracle Linux
         *  8.6
         *  2029-07-31
         *  2032-07-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Oracle Linux
         *  8.5
         *  2029-07-31
         *  2032-07-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Oracle Linux
         *  8.4
         *  2029-07-31
         *  2032-07-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Oracle Linux
         *  8.3
         *  2029-07-31
         *  2032-07-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Oracle Linux
         *  8.2
         *  2029-07-31
         *  2032-07-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Oracle Linux
         *  8.1
         *  2029-07-31
         *  2032-07-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Oracle Linux
         *  8.0
         *  2029-07-31
         *  2032-07-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_

.. dropdown:: Red Hat Enterprise Linux (RHEL)
   :name: os-rhel
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `RHEL <https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux>`_.

   RHEL is suitable for a same-host migration from LOCKSS 1.x to LOCKSS 2.x [#fnsamehostmigration]_.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  RHEL
         *  10.1
         *  2030-05-31
         *  2035-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel-iptables]_
      *  *  RHEL
         *  10.0
         *  2030-05-31
         *  2035-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel-iptables]_
      *  *  RHEL
         *  9.7
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  RHEL
         *  9.6
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  RHEL
         *  9.5
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  RHEL
         *  9.4
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  RHEL
         *  9.3
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  RHEL
         *  9.2
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  RHEL
         *  9.1
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  RHEL
         *  9.0
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  RHEL
         *  8.10
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  RHEL
         *  8.9
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  RHEL
         *  8.8
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  RHEL
         *  8.7
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  RHEL
         *  8.6
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  RHEL
         *  8.5
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  RHEL
         *  8.4
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  RHEL
         *  8.3
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  RHEL
         *  8.2
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  RHEL
         *  8.1
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  RHEL
         *  8.0
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_

.. dropdown:: Rocky Linux
   :name: os-rocky-linux
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Rocky Linux <https://rockylinux.org/>`_.

   Rocky Linux is suitable for a same-host migration from LOCKSS 1.x to LOCKSS 2.x [#fnsamehostmigration]_.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  Rocky Linux
         *  10.1
         *  2030-05-31
         *  2035-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel-iptables]_
      *  *  Rocky Linux
         *  10.0
         *  2030-05-31
         *  2035-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel-iptables]_
      *  *  Rocky Linux
         *  9.7
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  Rocky Linux
         *  9.6
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  Rocky Linux
         *  9.5
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  Rocky Linux
         *  9.4
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  Rocky Linux
         *  9.3
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  Rocky Linux
         *  9.2
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  Rocky Linux
         *  9.1
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  Rocky Linux
         *  9.0
         *  2027-05-31
         *  2032-05-31
         *  
      *  *  Rocky Linux
         *  8.10
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Rocky Linux
         *  8.9
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Rocky Linux
         *  8.8
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Rocky Linux
         *  8.7
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Rocky Linux
         *  8.6
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Rocky Linux
         *  8.5
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Rocky Linux
         *  8.4
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_
      *  *  Rocky Linux
         *  8.3
         *  :octicon:`alert-fill` 2024-05-31
         *  2029-05-31
         *  :bdg-info-line:`footnote` [#fn-kernel54]_

.. dropdown:: SUSE Linux Enterprise Server (SLES) :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-sles
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `SLES <https://www.suse.com/products/server/>`_.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  SLES
         *  15.7
         *  2031-07-31
         *  2034-07-31
         *  
      *  *  SLES
         *  15.6
         *  :octicon:`alert-fill` 2025-12-31
         *  2028-06-30
         *  
      *  *  SLES
         *  15.5
         *  :octicon:`alert-fill` 2024-12-31
         *  2027-12-31
         *  
      *  *  SLES
         *  15.4
         *  :octicon:`alert-fill` 2023-12-31
         *  2026-12-31
         *  

.. dropdown:: Ubuntu :bdg-success-line:`new since LOCKSS 1.x`
   :name: os-ubuntu
   :animate: fade-in-slide-down

   LOCKSS 2.x is compatible with `Ubuntu <https://ubuntu.com/>`_.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  Ubuntu
         *  25.10
         *  :octicon:`alert` 2026-07-01
         *  :octicon:`alert` 2026-07-01
         *  
      *  *  Ubuntu
         *  24.04 LTS
         *  2029-04-25
         *  2029-04-25
         *  
      *  *  Ubuntu
         *  22.04 LTS
         *  :octicon:`alert-fill` 2024-09-30
         *  2027-04-01
         *  

----------------------------
Unsuitable Operating Systems
----------------------------

The following operating systems are unsuitable for use with LOCKSS 2.x because they are at end of life.

.. dropdown:: CentOS Linux :bdg-danger-line:`end of life`
   :name: os-centos-linux
   :animate: fade-in-slide-down

   .. warning::

      `CentOS Linux <https://www.centos.org/centos-linux/>`_ is at end of life and is **not suitable** for use with LOCKSS 2.x.

   .. tip::

      If you are currently running LOCKSS 1.x on a CentOS Linux host, we recommend a :doc:`new-host migration to LOCKSS 2.x <lockss-portal:migration/index>`. However, if you perform a :doc:`same-host migration to LOCKSS 2.x <lockss-portal:migration/index>`, you must upgrade your host to a newer operating system in the RHEL family first, such as :ref:`os-rocky-linux`, :ref:`os-almalinux`, :ref:`os-oracle-linux`, or :ref:`os-rhel`. See `OS Upgrades <https://github.com/lockss/community/wiki/OS-Upgrades>`_ in the LOCKSS Community Wiki for guidance.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  CentOS Linux
         *  8.5
         *  :octicon:`alert-fill` 2021-12-31
         *  :octicon:`alert-fill` 2021-12-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  8.4
         *  :octicon:`alert-fill` 2021-12-31
         *  :octicon:`alert-fill` 2021-12-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  8.3
         *  :octicon:`alert-fill` 2021-12-31
         *  :octicon:`alert-fill` 2021-12-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  8.2
         *  :octicon:`alert-fill` 2021-12-31
         *  :octicon:`alert-fill` 2021-12-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  8.1
         *  :octicon:`alert-fill` 2021-12-31
         *  :octicon:`alert-fill` 2021-12-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  8.0
         *  :octicon:`alert-fill` 2021-12-31
         *  :octicon:`alert-fill` 2021-12-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  7.9
         *  :octicon:`alert-fill` 2020-08-06
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  7.8
         *  :octicon:`alert-fill` 2020-08-06
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  7.7
         *  :octicon:`alert-fill` 2020-08-06
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  7.6
         *  :octicon:`alert-fill` 2020-08-06
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  7.5
         *  :octicon:`alert-fill` 2020-08-06
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  7.4
         *  :octicon:`alert-fill` 2020-08-06
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  7.3
         *  :octicon:`alert-fill` 2020-08-06
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  7.2
         *  :octicon:`alert-fill` 2020-08-06
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  7.1
         *  :octicon:`alert-fill` 2020-08-06
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  7.0
         *  :octicon:`alert-fill` 2020-08-06
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  6.10
         *  :octicon:`alert-fill` 2017-05-10
         *  :octicon:`alert-fill` 2020-11-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  6.9
         *  :octicon:`alert-fill` 2017-05-10
         *  :octicon:`alert-fill` 2020-11-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  6.8
         *  :octicon:`alert-fill` 2017-05-10
         *  :octicon:`alert-fill` 2020-11-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  6.7
         *  :octicon:`alert-fill` 2017-05-10
         *  :octicon:`alert-fill` 2020-11-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  6.6
         *  :octicon:`alert-fill` 2017-05-10
         *  :octicon:`alert-fill` 2020-11-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  6.5
         *  :octicon:`alert-fill` 2017-05-10
         *  :octicon:`alert-fill` 2020-11-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  6.4
         *  :octicon:`alert-fill` 2017-05-10
         *  :octicon:`alert-fill` 2020-11-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  6.3
         *  :octicon:`alert-fill` 2017-05-10
         *  :octicon:`alert-fill` 2020-11-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  6.2
         *  :octicon:`alert-fill` 2017-05-10
         *  :octicon:`alert-fill` 2020-11-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  6.1
         *  :octicon:`alert-fill` 2017-05-10
         *  :octicon:`alert-fill` 2020-11-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  6.0
         *  :octicon:`alert-fill` 2017-05-10
         *  :octicon:`alert-fill` 2020-11-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  5.11
         *  :octicon:`alert-fill` 2014-01-31
         *  :octicon:`alert-fill` 2017-03-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  5.10
         *  :octicon:`alert-fill` 2014-01-31
         *  :octicon:`alert-fill` 2017-03-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  5.9
         *  :octicon:`alert-fill` 2014-01-31
         *  :octicon:`alert-fill` 2017-03-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  5.8
         *  :octicon:`alert-fill` 2014-01-31
         *  :octicon:`alert-fill` 2017-03-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  5.7
         *  :octicon:`alert-fill` 2014-01-31
         *  :octicon:`alert-fill` 2017-03-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  5.6
         *  :octicon:`alert-fill` 2014-01-31
         *  :octicon:`alert-fill` 2017-03-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  5.5
         *  :octicon:`alert-fill` 2014-01-31
         *  :octicon:`alert-fill` 2017-03-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  5.4
         *  :octicon:`alert-fill` 2014-01-31
         *  :octicon:`alert-fill` 2017-03-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  5.3
         *  :octicon:`alert-fill` 2014-01-31
         *  :octicon:`alert-fill` 2017-03-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  5.2
         *  :octicon:`alert-fill` 2014-01-31
         *  :octicon:`alert-fill` 2017-03-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  5.1
         *  :octicon:`alert-fill` 2014-01-31
         *  :octicon:`alert-fill` 2017-03-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  CentOS Linux
         *  5.0
         *  :octicon:`alert-fill` 2014-01-31
         *  :octicon:`alert-fill` 2017-03-31
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`

.. dropdown:: EuroLinux :bdg-danger-line:`end of life`
   :name: os-eurolinux
   :animate: fade-in-slide-down

   .. warning::

      LOCKSS 2.x was compatible with `EuroLinux <https://docs.euro-linux.com/>`_, but EuroLinux was discontinued as of November 2024 and is therefore **not suitable** for use with LOCKSS 2.x. `EuroLinux users are urged to migrate to Rocky Linux. <https://docs.euro-linux.com/HowTo/migrate_to_rocky_linux/>`_

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  EuroLinux
         *  9.4
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  9.3
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  9.2
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  9.1
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  9.0
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  8.10
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  8.9
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  8.8
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  8.7
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  8.6
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  8.5
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  8.4
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  8.3
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  8.2
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  8.1
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  EuroLinux
         *  8.0
         *  :octicon:`alert-fill` 2024-10-23
         *  :octicon:`alert-fill` 2024-11-03
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`

.. dropdown:: Scientific Linux :bdg-danger-line:`end of life`
   :name: os-scientific-linux
   :animate: fade-in-slide-down

   .. warning::

      `Scientific Linux <https://scientificlinux.org/>`_ is at end of life and is **not suitable** for use with LOCKSS 2.x.

   .. list-table::
      :header-rows: 1

      *  *  Operating System
         *  Version
         *  Active Support
         *  Security Support
         *  Notes
      *  *  Scientific Linux
         *  7.9
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  Scientific Linux
         *  7.8
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  Scientific Linux
         *  7.7
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  Scientific Linux
         *  7.6
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  Scientific Linux
         *  7.5
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  Scientific Linux
         *  7.4
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  Scientific Linux
         *  7.3
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  Scientific Linux
         *  7.2
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  Scientific Linux
         *  7.1
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`
      *  *  Scientific Linux
         *  7.0
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`alert-fill` 2024-06-30
         *  :octicon:`x-circle-fill` :bdg-danger:`end of life`

----

.. rubric:: Footnotes

.. [#fn-k3s-os]

   Reference: https://docs.k3s.io/installation/requirements#operating-systems

.. [#fnsamehostmigration]

   Reference: :doc:`lockss-portal:migration/index`

.. [#fn-kernel54]

   To meet the :ref:`Host` prerequisites with this operating system, you may need to install a Linux kernel version 5.4. See :doc:`/sysadmin/kernel54`.

.. [#fn-kernel-iptables]

   To meet the :ref:`Host` prerequisites for this operating system, you may need to install the ``ip_tables`` loadable kernel module. See :doc:`/sysadmin/kernel-iptables`.
