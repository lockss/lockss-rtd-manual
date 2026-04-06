.. index:: system prerequisites

====================
System Prerequisites
====================

.. only:: html and not singlehtml

   .. sidebar::

      .. contents:: Section Table of Contents
         :local:
         :depth: 2
         :backlinks: none

|LOCKSS| requires a **Linux** host (either a physical machine or a virtual machine), with **at least some locally-attached storage**. This section discusses the host (CPU, memory, Linux, etc.) and storage prerequisites for LOCKSS |LATEST_MINOR|, which vary depending on the scope of your application.

.. index:: system prerequisites; host

------------------
Host Prerequisites
------------------

.. index:: system prerequisites; CPU

CPU Prerequisites
=================

LOCKSS |LATEST_MINOR| runs on a **64-bit CPU** with at least **4 CPU cores**, preferably 8, depending on how many :doc:`components` you choose to run.

.. index:: system prerequisites; memory

Memory Prerequisites
====================

Likewise, the memory requirements also depend on which :doc:`components` you choose to run. We recommend **32 GB of memory** for typical applications, or more for hosts involved in computing-heavy applications like the Global LOCKSS Network (GLN) or CLOCKSS.

.. index:: system prerequisites; operating system

Operating System Prerequisites
==============================

LOCKSS requires a Linux distribution that is compatible with :term:`K3s`, the :term:`Kubernetes` distribution the :term:`LOCKSS stack` runs on. More specifically, LOCKSS |LATEST_MINOR| uses K3s |K3S_MINOR|.

This prerequisite is met by operating systems listed in the :ref:`Compatible Operating Systems` appendix (with some adjustments for some versions), including AlmaLinux OS, Arch Linux, CentOS Stream, Debian, Fedora Linux, Linux Mint, OpenSUSE, Oracle Linux, Red Hat Enterprise Linux (RHEL), Rocky Linux, SUSE Linux Enterprise Server (SLES), and Ubuntu.

.. index:: system prerequisites; Linux kernel

Linux Kernel Prerequisites
==========================

Most versions of Linux distributions in the :ref:`Compatible Operating Systems` appendix satisfy the **Linux kernel prerequisites** for LOCKSS |LATEST_MINOR| out of the box:

1. .. dropdown:: Linux kernel 5.4 or later is required
      :name: prerequisites-kernel54
      :animate: fade-in-slide-down

      Linux kernel 5.4 or later is **required**.

      .. include:: /sysadmin/kernel54-test.rst

      If the host does not satify the Linux kernel version requirement, see :doc:`/sysadmin/kernel54`.

      .. include:: /sysadmin/kernel54-tip.rst

2. .. dropdown:: ``ip_tables`` loadable kernel module is **required**
      :name: prerequisites-iptables-lkm
      :animate: fade-in-slide-down

      The ``ip_tables`` loadable kernel module is **required**, even if :term:`iptables` or :term:`nftables` are not installed on the host.

      .. include:: /sysadmin/kernel-iptables-test.rst

      If installing the ``ip_tables`` loadable kernel module is required, see :doc:`/sysadmin/kernel-iptables`.

      .. include:: /sysadmin/kernel-iptables-tip.rst

.. index:: system prerequisites; system software

System Software Prerequisites
=============================

:doc:`/installing/index` and :doc:`/upgrading/index` uses the :term:`LOCKSS Downloader`, which has basic **system software prerequisites** that are met by almost any Linux distribution:

1. .. dropdown:: Curl or Wget is required
      :name: prerequisites-fetcher
      :animate: fade-in-slide-down

      At least one of :term:`Curl` or :term:`Wget` is **required**. You can check by typing ``curl --version`` or ``wget --version`` at the host's command line.

      *  If either outputs a valid version message, the host satisfies the fetcher requirement.

      *  If both output an error message, the host does not satisfy the fetcher requirement. See :doc:`/sysadmin/curl` or :doc:`/sysadmin/wget`.

2. .. dropdown:: Tar and Unzip are required
      :name: prerequisites-archiver
      :animate: fade-in-slide-down

      Both Tar (:program:`tar` or :program:`gtar`) and Unzip (:program:`unzip`) are **required**. You can check by typing ``tar --version`` (or ``gtar --version``) and ``unzip --version`` at the host's command line.

      *  If both output a valid version message, the host satisfies the archiver requirement.

      *  If either outputs an error message, the host does not satisfy the archiver requirement. See :doc:`/sysadmin/tar` or :doc:`/sysadmin/unzip`.

---------------------
Storage Prerequisites
---------------------

The LOCKSS system makes use of three kinds of **storage**:

.. list-table::
   :header-rows: 1

   *  *  Storage type
      *  Primary use
      *  Prerequisites section
   *  *  :term:`System storage`
      *  Software and related assets
      *  :numref:`System Storage Prerequisites` (:ref:`System Storage Prerequisites`)
   *  *  :term:`Operating storage`
      *  Internal :term:`stack <LOCKSS stack>` data (other than preserved content)
      *  :numref:`Operating Storage Prerequisites` (:ref:`Operating Storage Prerequisites`)
   *  *  :term:`Content storage`
      *  Preserved content
      *  :numref:`Content Storage Prerequisites` (:ref:`Content Storage Prerequisites`)

.. index:: system prerequisites; system storage, system storage; prerequisites

System Storage Prerequisites
============================

.. include:: /glossary/system-storage.rst

The LOCKSS stack makes use of system storage in three ways:

.. list-table::
   :header-rows: 1

   *  *  System storage area
      *  Primary use
      *  Configuration step
   *  *  :term:`K3s data directory`
      *  Downloaded containers, :term:`K3s` configuration
      *  :numref:`Installing K3s` (:ref:`Installing K3s`)
   *  *  :ref:`LOCKSS Installer Directory`
      *  LOCKSS Installer software, LOCKSS stack configuration
      *  :numref:`Running the LOCKSS Downloader` (:ref:`Running the LOCKSS Downloader`)
   *  *  Miscellaneous system storage
      *  System software that may be installed as part of :doc:`/installing/index`
      *  n/a

The most significant portion of :term:`system storage` used by the LOCKSS stack is the :term:`K3s data directory`.

**System storage prerequisites** are as follows:

1. .. dropdown:: K3s data directory must be local
      :name: prerequisites-k3s-nfs
      :animate: fade-in-slide-down

      The :term:`K3s data directory` **must be local**, in other words cannot be backed by NFS or other non-local filesystems.

2. .. dropdown:: K3s data directory cannot be backed by legacy XFS with ``ftype=0``
      :name: prerequisites-k3s-xfs
      :animate: fade-in-slide-down

      The :term:`K3s data directory` **cannot be backed by a legacy XFS filesystem** with ``ftype=0``.

      This is expected to be an issue only for installations of LOCKSS 1.x using XFS filesystems old enough to have ``ftype=0``, looking to install LOCKSS |LATEST_MINOR| as part of a :doc:`same-host migration <lockss-portal:migration/index>`. Alternatives in this case include a :doc:`new-host migration <lockss-portal:migration/index>`, or a potential workaround; see :doc:`/troubleshooting/xfs`.

3. .. dropdown:: K3s data directory size requirements
      :name: prerequisites-k3s-size
      :animate: fade-in-slide-down

      The :term:`K3s data directory` can grow large and requires **at least 50 GB of space**.

.. index:: system prerequisites; operating storage, operating storage; prerequisites

Operating Storage Prerequisites
===============================

.. include:: /glossary/operating-storage.rst

Operating storage consists of three storage areas:

.. list-table::
   :header-rows: 1

   *  *  Operating storage area
      *  Primary use
      *  Configuration step
   *  *  :term:`State data storage area`
      *  Database data, state files
      *  :numref:`State Data Storage Area Settings` (:ref:`State Data Storage Area Settings`)
   *  *  :term:`Log storage area`
      *  Log files
      *  :numref:`Log Storage Area Settings` (:ref:`Log Storage Area Settings`)
   *  *  :term:`Temporary storage area`
      *  Temporary files and other working data
      *  :numref:`Temporary Storage Area Settings` (:ref:`Temporary Storage Area Settings`)

**Operating storage prerequisites** are as follows:

1. .. dropdown:: Local operating storage is strongly recommended
      :name: prerequisites-operating-storage-local
      :animate: fade-in-slide-down

      For all operating storage, **local storage is strongly recommended**, in other words NFS or other non-local filesystems are strongly discouraged, as remote filesystems for operating storage can negatively impact the performance of the LOCKSS stack.

2. .. dropdown:: State data storage area size requirements
      :name: prerequisites-state-data-storage-size
      :animate: fade-in-slide-down

      State data storage usage is dominated by the :ref:`PostgreSQL` database, which can grow to very different sizes depending on the scope of your application, for example how many individual :term:`artifacts <artifact>` (data objects) are preserved in the :ref:`LOCKSS Repository Service` and to what extent the :ref:`LOCKSS Metadata Service` is used. We propose the following guidelines:

      *  Small state data profile: A modest application with thousands of :term:`archival units <archival unit>`, with reasonable file sizes (for example, less than 2 GB) and number of files per AU. For this profile, we recommend **at least 50 GB of state data storage**.

      *  Medium state data profile: An application that is expected to exceed one of the parameters for a small state data profile, perhaps involving tens of thousands of AUs, some large files in the tens of gigabytes, or AUs with tens of thousands of files. For this profile, we recommend  **at least 150 GB of state data storage**.

      *  Large state data profile: An intensive application with extensive metadata extraction, perhaps like the Global LOCKSS Network (GLN) or CLOCKSS. For this profile, we recommend  **at least 500 GB of state data storage**.

3. .. dropdown:: Temporary storage area size requirements
      :name: prerequisites-temporary-storage-size
      :animate: fade-in-slide-down

      Depending on the characteristics of the preservation activities undertaken by the system, content processing may require a substantial amount of temporary space. As a guideline, we recommend either **50 GB of temporary storage**, or **about three times as much temporary storage as the largest individual file expected to be preserved**, whichever is larger.

.. index:: content storage; prerequisites

.. index:: system prerequisites; content storage, content storage; prerequisites

Content Storage Prerequisites
=============================

.. include:: /glossary/content-storage.rst

Content storage can be backed by NFS or other non-local filesystems, although locally-attached storage is more performant.

In total, the content storage areas need to be **large enough to hold all the content to be preserved in the node**.

The list of :term:`content storage areas <content storage area>` is configurable in :numref:`Content Storage Area Settings` (:ref:`Content Storage Area Settings`).

.. index:: system prerequisites; miscellaneous prerequisites

---------------------------
Miscellaneous Prerequisites
---------------------------

.. index:: system prerequisites; networking considerations

Networking Considerations
=========================

Internally, :term:`K3s` uses the private subnets 10.42.0.0/16 and 10.43.0.0/16 (the IP addresses from 10.42.0.0 through 10.43.255.255) to allocate IP addresses to :term:`containers <container>`. The networking infrastructure at some institutions may include host-based :term:`firewall` rules that can inadvertently block K3s' internal communication mechanisms. If your institution does this, you will need to exclude 10.42.0.0/16 and 10.43.0.0/16 (or more succinctly, 10.42.0.0/15) from these rules. What to do will vary depending on your individual situation.

.. index:: system prerequisites; configuration management

Configuration Management Considerations
=======================================

Some :term:`firewall` and :term:`iptables` enforcement features of :term:`configuration management systems <configuration management system>` such as `Puppet <https://puppet.com/>`_, `Ansible <https://www.ansible.com/>`_, `Chef <https://www.chef.io/>`_, or `Salt <https://saltproject.io/>`_, are incompatible with :term:`K3s`. For example, Puppet's ``puppetlabs-firewall`` module sometimes causes K3s to be non-functional after a reboot, requiring killing and restarting the K3s systemd service. What to do will vary depending on your individual situation.

----

.. admonition:: What's the Minimum for Experimentation?

   To review the installation instructions and test the installation of K3s in various operating systems, we routinely install and bring up minimal LOCKSS |LATEST_MINOR|, with no metadata services or Web replay engines, and with empty embedded PostgreSQL database, in Vagrant virtual machines with Virtualbox, using 2 CPU cores and 3 GB of memory. These minimal VMs would not support a production load, but it can be a useful tool to try out the installation instructions or evaluate the system.
