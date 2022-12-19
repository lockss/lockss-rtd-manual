================
Operating System
================

The LOCKSS system requires a **64-bit Linux** host (physical or virtual) compatible with `K3s <https://k3s.io/>`_, a lightweight Kubernetes distribution by `Rancher <https://rancher.com/>`_. The K3s documentation states [#fnk3sos]_ that "K3s is expected to work on most modern Linux systems", and that "Some OSs have specific requirements" (which are documented in this manual and integrated into the :program:`lockss-installer` scripts).

The LOCKSS team has successfully tested the LOCKSS system installation process on many flavors of Linux, some of which are listed below:

.. dropdown:: AlmaLinux

   The LOCKSS system is compatible with `AlmaLinux <https://almalinux.org/>`_:

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   AlmaLinux           9.1       2027-05-31     2032-05-31
   AlmaLinux           9.0       2027-05-31     2032-05-31
   AlmaLinux           8.7       2024-05-31     2029-05-31
   AlmaLinux           8.6       2024-05-31     2029-05-31
   AlmaLinux           8.5       2024-05-31     2029-05-31
   AlmaLinux           8.4       2024-05-31     2029-05-31
   AlmaLinux           8.3       2024-05-31     2029-05-31
   =================== ========= ============== ================ =====

.. dropdown:: Arch Linux

   The LOCKSS system is compatible with `Arch Linux <https://archlinux.org/>`_:

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Arch Linux          rolling
   =================== ========= ============== ================ =====

.. dropdown:: CentOS

   .. caution::

      We no longer recommend CentOS for new installations; we recommend Rocky Linux instead.

   The LOCKSS system is compatible with `CentOS <https://centos.org>`_:

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   CentOS Stream       rolling
   CentOS Linux        7.9       2020-08-06     2024-06-30       :bdg-danger:`EOL`
   CentOS Linux        7.8       2020-08-06     2024-06-30       :bdg-danger:`EOL`
   CentOS Linux        7.7       2020-08-06     2024-06-30       :bdg-danger:`EOL`
   CentOS Linux        7.6       2020-08-06     2024-06-30       :bdg-danger:`EOL`
   CentOS Linux        7.5       2020-08-06     2024-06-30       :bdg-danger:`EOL`
   CentOS Linux        7.4       2020-08-06     2024-06-30       :bdg-danger:`EOL`
   CentOS Linux        7.3       2020-08-06     2024-06-30       :bdg-danger:`EOL`
   =================== ========= ============== ================ =====

.. dropdown:: Debian

   The LOCKSS system is compatible with `Debian <https://www.debian.org/>`_:

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Debian              11.5      June 2026      2026-08-15
   Debian              11.4      June 2026      2026-08-15
   Debian              11.3      June 2026      2026-08-15
   Debian              11.2      June 2026      2026-08-15
   Debian              11.1      June 2026      2026-08-15
   Debian              11.0      June 2026      2026-08-15
   Debian              10.11     2024-06-30     2024-06-01
   Debian              10.10     2024-06-30     2024-06-01
   Debian              10.9      2024-06-30     2024-06-01
   Debian              10.8      2024-06-30     2024-06-01
   Debian              10.7      2024-06-30     2024-06-01
   Debian              10.6      2024-06-30     2024-06-01
   Debian              10.5      2024-06-30     2024-06-01
   Debian              10.4      2024-06-30     2024-06-01
   Debian              10.3      2024-06-30     2024-06-01
   Debian              10.2      2024-06-30     2024-06-01
   Debian              10.1      2024-06-30     2024-06-01
   Debian              10.0      2024-06-30     2024-06-01
   =================== ========= ============== ================ =====

.. dropdown:: EuroLinux

   The LOCKSS system is compatible with `EuroLinux <https://en.euro-linux.com/eurolinux>`_:

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   EuroLinux           9.1       2032-05-31     2032-06-30
   EuroLinux           9.0       2032-05-31     2032-06-30
   EuroLinux           8.6       2029-03-01     2029-06-30
   EuroLinux           8.5       2029-03-01     2029-06-30
   EuroLinux           8.4       2029-03-01     2029-06-30
   EuroLinux           8.3       2029-03-01     2029-06-30
   EuroLinux           7.9       2024-07-31     2024-07-31
   EuroLinux           7.8       2024-07-31     2024-07-31
   EuroLinux           7.7       2024-07-31     2024-07-31
   EuroLinux           7.6       2024-07-31     2024-07-31
   =================== ========= ============== ================ =====

.. dropdown:: Fedora Linux

   The LOCKSS system is compatible with `Fedora Linux <https://getfedora.org/>`_:

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Fedora Linux        37        2023-12-15     2023-12-15
   Fedora Linux        36        2023-05-16     2023-05-16
   =================== ========= ============== ================ =====

.. dropdown:: Linux Mint

   The LOCKSS system is compatible with `Linux Mint <https://linuxmint.com/>`_:

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Linux Mint          21        Yes            2027-04-01
   Linux Mint          20.3      Yes            2025-04-01
   Linux Mint          20.2      Yes            2025-04-01
   Linux Mint          20.1      No             2025-04-01       :bdg-danger:`EOL`
   Linux Mint          20        No             2025-04-01       :bdg-danger:`EOL`
   =================== ========= ============== ================ =====

.. dropdown:: OpenSUSE

   The LOCKSS system is compatible with `OpenSUSE <https://www.opensuse.org/>`_:

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   OpenSUSE Tumbleweed rolling
   OpenSUSE Leap       15.4      2023-12-01     2023-12-01
   =================== ========= ============== ================ =====

.. dropdown:: Oracle Linux

   The LOCKSS system is compatible with `Oracle Linux <https://www.oracle.com/linux>`_:

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Oracle Linux        9.0       2032-07-01     2034-06-01
   Oracle Linux        8.7       2029-07-01     2029-07-01
   Oracle Linux        8.6       2029-07-01     2029-07-01
   Oracle Linux        8.5       2029-07-01     2029-07-01
   Oracle Linux        8.4       2029-07-01     2029-07-01
   Oracle Linux        8.3       2029-07-01     2029-07-01
   Oracle Linux        8.2       2029-07-01     2029-07-01
   Oracle Linux        8.1       2029-07-01     2029-07-01
   Oracle Linux        7.9       2024-07-01     2026-06-01
   Oracle Linux        7.8       2024-07-01     2026-06-01
   Oracle Linux        7.7       2024-07-01     2026-06-01
   Oracle Linux        7.6       2024-07-01     2026-06-01
   =================== ========= ============== ================ =====

.. dropdown:: RHEL

   The LOCKSS system is compatible with `RHEL <https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux>`_:

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   RHEL                8.3       2024-05-31     2029-05-31
   =================== ========= ============== ================ =====

.. dropdown:: Rocky Linux

   .. tip::

      `Rocky Linux <https://rockylinux.org/>`_ is the operating system we currently recommend for new installations, and for existing installations based on CentOS or Scientific Linux.

   The LOCKSS system is compatible with `Rocky Linux <https://rockylinux.org/>`_:

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Rocky Linux         9.1       2025-05-31     2032-05-31
   Rocky Linux         9.0       2025-05-31     2032-05-31
   Rocky Linux         8.7       2024-05-31     2029-05-31
   Rocky Linux         8.6       2024-05-31     2029-05-31
   Rocky Linux         8.5       2024-05-31     2029-05-31
   Rocky Linux         8.4       2024-05-31     2029-05-31
   =================== ========= ============== ================ =====

.. dropdown:: Scientific Linux

   .. caution::

      We no longer recommend Scientific Linux for new installations; we recommend Rocky Linux instead.

   The LOCKSS system is compatible with `Scientific Linux <https://scientificlinux.org/>`_:

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Scientific Linux    7.9       2024-06-30     2024-06-30
   Scientific Linux    7.8       2024-06-30     2024-06-30
   Scientific Linux    7.7       2024-06-30     2024-06-30
   Scientific Linux    7.6       2024-06-30     2024-06-30
   =================== ========= ============== ================ =====

.. dropdown:: Ubuntu

   The LOCKSS system is compatible with `Ubuntu <https://ubuntu.com/>`_:

   =================== ========= ============== ================ =====
   Operating System    Version   Active Support Security Support Notes
   =================== ========= ============== ================ =====
   Ubuntu              22.10     2023-07-20     2023-07-20
   Ubuntu              22.04 LTS 2027-04-21     2032-04-01
   Ubuntu              20.04 LTS 2025-04-02     2030-04-01
   Ubuntu              18.04 LTS 2023-04-02     2028-04-01
   =================== ========= ============== ================ =====

The LOCKSS system can likely be installed successfully on slightly different versions of the Linux flavors above, as well as other Linux flavors altogether, including commercial variants like `RHEL <https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux>`_ or `SLES <https://www.suse.com/products/server>`_. We welcome reports of successful installations from the community so they can be added to the list above.

.. tip::

   `Rocky Linux <https://rockylinux.org/>`_ is the operating system we currently recommend for new installations, and for existing installations based on CentOS or Scientific Linux.

----

.. rubric:: Footnotes

.. [#fnk3sos]

   Reference: https://docs.k3s.io/installation/requirements#operating-systems
