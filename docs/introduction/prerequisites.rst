====================
System Prerequisites
====================

----
Host
----

The LOCKSS system runs in a **64-bit Linux** host (physical or virtual).

See the next section (:doc:`os`) for operating system choices.

---
CPU
---

The CPU requirements depend on which components of the LOCKSS system you choose to run. We recommend at least **4 CPU cores**, preferably 8.

------
Memory
------

Likewise, the memory requirements also depend on which components of the LOCKSS system you choose to run. We recommend at least **16 GB** of memory for modest applications, more for machines involved in sizeable applications like the Global LOCKSS Network.

-------
Storage
-------

LOCKSS makes use of several storage areas.  During configuration, the administrator must specify the location of these storage areas by supplying one or more directory paths. The default is to put all storage under a single directory, but different types of storage have different size and performance requirements and on a large system, if different types of storage are available it may be advantageous to place the storage areas on different devices:

*  **Content storage:** This is where all the preserved content is stored. Many LOCKSS systems preserve a large amount of content and, while not recommended, some sites find it necessary to use network-attached storage such as NFS for this. LOCKSS' audit activities involve nearly continuous reading of preserved content from storage; performance of the LOCKSS system will be significantly impacted, and performance of the storage device may be impacted, if using network-attached storage.

   The amount of space required depends on the amount of content that will be preserved. The content is efficiently stored in large, compressed WARC files. Unlike LOCKSS 1.x, inode usage is very low. Multiple content storage areas may be specified, and more can be added later.

*  **Data storage:** This is used for databases (unless using external PostgreSQL and/or Solr) and other state files. **We strongly recommend placing this on a filesystem with low latency, that is, locally-attached storage**, as performance will be severely impacted if on network-attached storage.

*  **Temporary storage:** The LOCKSS software makes heavy use of temporary storage. **We strongly recommend placing this on a filesystem with low latency, that is, locally-attached storage**, as performance will be severely impacted if on network-attached storage.

   .. caution::

      Depending on the characteristics of the preservation activities undertaken by the system, in some circumstances content processing may require a substantial amount of temporary space, up to tens of gigabytes. Do not use a RAM-based ``tmpfs`` volume, or a directory in a space-constrained partition, for temporary data storage.

*  **Log storage:** Service logs will be written to subdirectories of this storage area. We recommend placing this on a filesystem with low latency, that is, locally-attached storage.

----

.. admonition:: What's the Minimum for Experimentation?

   To review the installation instructions and test the installation of K3s in various operating systems, we routinely install and bring up minimal LOCKSS 2.0-alpha5 systems, with no metadata services or Web replay engines, and with empty embedded Postgres and Solr databases, in Vagrant virtual machines with Virtualbox using 2 CPU cores and 3 GB of memory. These minimal VMs would not support a production load, but it can be a useful tool to try out the installation instructions or evaluate the system.
