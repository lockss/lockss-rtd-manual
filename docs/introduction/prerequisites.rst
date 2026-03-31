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

|LOCKSS| |LATEST_MINOR| requires a **Linux** host (either a physical machine or a virtual machine), with **at least some locally-attached storage**. This section discusses the host (CPU, memory, Linux, etc.) and storage prerequisites for |LOCKSS| |LATEST_MINOR|, which vary depending on the scope of your application.

.. index:: system prerequisites; host

------------------
Host Prerequisites
------------------

.. index:: system prerequisites; CPU

CPU Prerequisites
=================

LOCKSS |LATEST_MINOR| runs on a **64-bit CPU** with at least **4 CPU cores**, preferably 8, depending on which :doc:`components` you choose to run.

.. index:: system prerequisites; memory

Memory Prerequisites
====================

Likewise, the memory requirements also depend on which :doc:`components` you choose to run. We recommend **32 GB** of memory for typical applications, or more for hosts involved in computing-heavy applications like the Global LOCKSS Network (GLN) or CLOCKSS.

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
      :name: prerequisites-iptables-lkm
      :animate: fade-in-slide-down

      .. note::

         Note the difference between the ``ip_tables`` (the loadable kernel module) and :term:`iptables` (the program).

      The ``ip_tables`` loadable kernel module is **required**, even if :term:`iptables` or :term:`nftables` are not installed on the host. You can check if the ``ip_tables`` loadable kernel module is available by typing:

      .. code-block:: shell

         modinfo ip_tables

      at the host's command line.

      *  If technical information about the module is output [#fn-iptables-lkm-example]_, the host satisfies the ``ip_tables`` loadable kernel module requirement.

      *  If an error message similar to the following is output:

         .. code-block:: text

            modinfo: ERROR: Module ip_tables not found.

         the host does not satisfy the ``ip_tables`` loadable kernel module requirement. See :doc:`/sysadmin/kernel-iptables`.

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

3. .. dropdown:: System storage size requirements
      :name: prerequisites-system-storage-size
      :animate: fade-in-slide-down

      FIXME

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

      For operating storage, **local storage is strongly recommended**, in other words NFS or other non-local filesystems are strongly discouraged, as remote filesystems for operating storage can negatively impact the performance of the LOCKSS stack.

2. .. dropdown:: Temporary storage area filesystem requirements
      :name: prerequisites-temporary-storage-size
      :animate: fade-in-slide-down

      Depending on the characteristics of the preservation activities undertaken by the system, in some circumstances content processing may require a substantial amount of temporary space, up to tens of gigabytes. A RAM-based ``tmpfs`` volume or a directory in a space-constrained partition are **not suitable for the temporary storage area**.

3. .. dropdown:: Operating storage size requirements
      :name: prerequisites-operating-storage-size
      :animate: fade-in-slide-down

      FIXME

.. index:: content storage; prerequisites

.. index:: system prerequisites; content storage, content storage; prerequisites

Content Storage Prerequisites
=============================

.. include:: /glossary/content-storage.rst

Content storage can be backed by NFS or other non-local filesystems, although locally-attached storage is more performant.

The list of :term:`content storage areas <content storage area>` is configurable in :numref:`Content Storage Areas` (:ref:`Content Storage Areas`).

FIXME

----

.. admonition:: What's the Minimum for Experimentation?

   To review the installation instructions and test the installation of K3s in various operating systems, we routinely install and bring up minimal LOCKSS |LATEST_MINOR|, with no metadata services or Web replay engines, and with empty embedded PostgreSQL database, in Vagrant virtual machines with Virtualbox, using 2 CPU cores and 3 GB of memory. These minimal VMs would not support a production load, but it can be a useful tool to try out the installation instructions or evaluate the system.

----

.. rubric:: Footnotes

.. [#fn-iptables-lkm-example]

   Sample output:

   .. literalinclude:: prerequisites-iptables-example.txt
      :language: text
