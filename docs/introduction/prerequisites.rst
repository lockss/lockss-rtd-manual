====================
System Prerequisites
====================

.. only:: html and not singlehtml

   .. sidebar::

      .. contents:: Section Table of Contents
         :local:
         :depth: 1
         :backlinks: none

This section describes the Linux host, CPU, memory, and storage prerequisites for LOCKSS |LATEST_MINOR|, which vary depending on the scope of your application.

----
Host
----

LOCKSS |LATEST_MINOR| requires a **Linux** host (physical machine or virtual machine), on one of many :ref:`Compatible Operating Systems`. The key prerequisite is that the Linux distribution must be compatible with `K3s <https://k3s.io/>`_, the lightweight open source Kubernetes distribution the LOCKSS stack runs on, which is true of many versions of AlmaLinux OS, Arch Linux, CentOS Stream, Debian, Fedora Linux, Linux Mint, OpenSUSE, Oracle Linux, Red Hat Enterprise Linux (RHEL), Rocky Linux, SUSE Linux Enterprise Server (SLES), and Ubuntu listed in the :doc:`/appendix/os` appendix.

Linux Kernel
============

Most versions of :ref:`Compatible Operating Systems` satisfy the **Linux kernel prerequisites** for LOCKSS |LATEST_MINOR| out of the box:

1. .. dropdown:: Linux kernel 5.4 or later is required
      :name: prerequisite-kernel54
      :animate: fade-in-slide-down

      Linux kernel 5.4 or later is **required**. You can check the Linux kernel version by typing:

      .. code-block:: shell

         uname --kernel-release

      or equivalently:

      .. code-block:: shell

         uname -r

      at the host's command line.

      *  If version 5.4 or later is output, the host satisfies the Linux kernel version requirement.

      *  If version 5.3 or earlier is output, the host does not satify the Linux kernel version requirement. See :doc:`/sysadmin/kernel54`.

2. .. dropdown:: ``ip_tables`` loadable kernel module is **required**
      :name: prerequisite-iptables-lkm
      :animate: fade-in-slide-down

      The ``ip_tables`` loadable kernel module is required, even if the programs :program:`iptables` or :program:`nftables` are not installed on the host. You can check if the ``ip_tables`` loadable kernel module is available by typing:

      .. code-block:: shell

         modinfo ip_tables

      at the host's command line.

      .. note::

         Note that in this context, the correct name is ``ip_tables`` (a loadable kernel module), not ``iptables`` (a program) as in many other contexts.

      *  If technical information about the module is output [#fn-iptables-example]_, the host satisfies the ``ip_tables`` loadable kernel module requirement.

      *  If an error message similar to the following is output:

         .. code-block:: text

            modinfo: ERROR: Module ip_tables not found.

         the host does not satisfy the ``ip_tables`` loadable kernel module requirement. See :doc:`/sysadmin/kernel-iptables`.

System Software
===============

:doc:`/installing/index` and :doc:`/upgrading/index` uses the LOCKSS Downloader, which has basic **system software prerequisites** that are met by almost any of the :ref:`Compatible Operating Systems`:

1. .. dropdown:: Curl or Wget is required
      :name: prerequisite-fetcher
      :animate: fade-in-slide-down

      At least one of Curl or Wget is **required**. You can check by typing ``curl --version`` or ``wget --version`` at the host's command line.

      *  If either outputs a valid version message, the host satisfies the fetcher requirement.

      *  If both output an error message, the host does not satisfy the fetcher requirement. See :doc:`/sysadmin/curl` or :doc:`/sysadmin/wget`.

2. .. dropdown:: Tar and Unzip are required
      :name: prerequisite-archiver
      :animate: fade-in-slide-down

      Both Tar (:program:`tar` or :program:`gtar`) and Unzip (:program:`unzip`) are **required**. You can check by typing ``tar --version`` (or ``gtar --version``) and ``unzip --version`` at the host's command line.

      *  If both output a valid version message, the host satisfies the archiver requirement.

      *  If either outputs an error message, the host does not satisfy the archiver requirement. See :doc:`/sysadmin/tar` or :doc:`/sysadmin/unzip`.

---
CPU
---

The LOCKSS system runs on a **64-bit CPU** with at least **4 CPU cores**, preferably 8, depending on which :doc:`components` you choose to run.

------
Memory
------

Likewise, the **memory** requirements also depend on which :doc:`components` you choose to run. We recommend **32 GB** of memory for typical applications, or more for machines involved in sizeable applications like the Global LOCKSS Network (GLN) or CLOCKSS.

-------
Storage
-------

The LOCKSS system's **storage** needs are three-fold:

.. list-table::
   :header-rows: 1

   *  *  Storage type
      *  Primary use
   *  *  :ref:`System Storage`
      *  Software and related assets
   *  *  :ref:`Operating Storage`
      *  Internal stack data (other than preserved content)
   *  *  :ref:`Content Storage`
      *  Preserved content

During :doc:`configuration </configuring>`, you will specify the location of the :ref:`Operating Storage` and :ref:`Content Storage` areas, as well as the most significant :ref:`System Storage` area (the K3s state data directory [#fn-k3s-data-directory]_), by supplying directory paths to the installation and configuration scripts.

System Storage
==============

**System storage** is storage space needed for installed software, downloaded containers, data generated by the underlying Kubernetes environment, etc. The LOCKSS stack makes use of three areas of system storage:

.. list-table::
   :header-rows: 1

   *  *  System storage area
      *  Primary use
      *  Configuration step
   *  *  K3s data directory [#fn-k3s-data-directory]_
      *  Downloaded containers, Kubernetes configuration
      *  :numref:`Installing K3s` (:ref:`Installing K3s`)
         
         Default: :file:`/var/lib/rancher/k3s`
   *  *  :ref:`LOCKSS Installer Directory`
      *  LOCKSS Installer software, LOCKSS stack configuration
      *  :numref:`Running the LOCKSS Downloader` (:ref:`Running the LOCKSS Downloader`)
         
         Default: :ref:`Default LOCKSS Installer Directory`
   *  *  Miscellaneous system storage
      *  System software that may be installed as part of :doc:`/installing/index`
      *  n/a

The most significant portion of system storage used by the LOCKSS stack is the **K3s data directory** [#fn-k3s-data-directory]_, which by default is :file:`/var/lib/rancher/k3s`.

**System storage prerequisites** are as follows:

1. .. dropdown:: System storage cannot be backed by NFS
      :name: prerequisite-system-storage-local
      :animate: fade-in-slide-down

      All system storage **must be local**, in other words cannot be backed by NFS or other non-local filesystems. In particular, this applies to the **K3s data directory** [#fn-k3s-data-directory]_. (This requirement does not extend to :ref:`Content Storage`.)

2. .. dropdown:: K3s Data Directory cannot be backed by legacy XFS with ``ftype=0``
      :name: prerequisite-k3s-legacy-xfs
      :animate: fade-in-slide-down

      The K3s data directory [#fn-k3s-data-directory]_ **cannot be backed by a legacy XFS filesystem** with ``ftype=0``. This is expected to be an issue only for older installations of LOCKSS 1.x with XFS filesystems performing a :doc:`same-host migrating to LOCKSS 2.x <lockss-portal:migration/index>`. For more details, see :doc:`/troubleshooting/xfs`.

3. .. dropdown:: System storage size requirements
      :name: prerequisite-system-storage-size
      :animate: fade-in-slide-down

      FIXME

Operating Storage
=================

FIXME

**Operating storage** (storage space devoted to the internal operating needs of the LOCKSS stack, such as database data, state files, log files, temporary files, off-heap runtime data, etc.) consists of three distinct storage areas:

.. list-table::
   :header-rows: 1

   *  *  Operating storage area
      *  Primary use
      *  Configuration step
   *  *  State data storage area
      *  Database data and state files
      *  :numref:`State Data Storage Area` (:ref:`State Data Storage Area`)
   *  *  Log storage area
      *  Log files
      *  :numref:`Log Storage Area` (:ref:`Log Storage Area`)
   *  *  Temporary storage area
      *  Temporary file and other working data
      *  :numref:`Temporary Storage Area` (:ref:`Temporary Storage Area`)

Requirements for operating storage are as follows:

1. .. dropdown:: Local operating storage is strongly recommended
      :name: prerequisite-operating-storage-local
      :animate: fade-in-slide-down

      For operating storage, **local storage is strongly recommended**, in other words NFS or other non-local filesystems are strongly discouraged, as remote filesystems can dramatically impact the performance of the LOCKSS system.

2. .. dropdown:: Temporary storage area filesystem requirements
      :name: prerequisite-temporary-storage-size
      :animate: fade-in-slide-down

      Depending on the characteristics of the preservation activities undertaken by the system, in some circumstances content processing may require a substantial amount of temporary space, up to tens of gigabytes. A RAM-based ``tmpfs`` volume or a directory in a space-constrained partition are **not suitable for the temporary storage area**.

3. .. dropdown:: Operating storage size requirements
      :name: prerequisite-operating-storage-size
      :animate: fade-in-slide-down

      FIXME

Content Storage
===============

**Content storage** (storage space devoted to the content being preserved by the LOCKSS stack) can be backed by NFS or other non-local filesystems (although locally-attached storage is more performant), and can consist of multiple content storage areas (for example multiple RAID arrays).

The list of content storage areas is configurable in :ref:`Content Storage Areas` (:numref:`Content Storage Areas`).

FIXME

----

.. admonition:: What's the Minimum for Experimentation?

   To review the installation instructions and test the installation of K3s in various operating systems, we routinely install and bring up minimal LOCKSS |LATEST_MINOR|, with no metadata services or Web replay engines, and with empty embedded PostgreSQL and Solr databases, in Vagrant virtual machines with Virtualbox using 2 CPU cores and 3 GB of memory. These minimal VMs would not support a production load, but it can be a useful tool to try out the installation instructions or evaluate the system.

----

.. rubric:: Footnotes

.. [#fn-iptables-example]

   Sample output:

   .. literalinclude:: prerequisites-iptables-example.txt
      :language: text

.. [#fn-k3s-data-directory]

   `K3s <https://k3s.io/>`_ (the Kubernetes distribution on which the containers of the LOCKSS stack run) downloads containers and stores configuration data in the **K3s Data Directory**. The location of the K3s data directory is configurable in the LOCKSS Installer (see :numref:`Installing K3s`, :ref:`Installing K3s`), by default :file:`/var/lib/rancher/k3s`.
