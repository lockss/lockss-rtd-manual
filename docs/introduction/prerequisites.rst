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

Likewise, the memory requirements also depend on which components of the LOCKSS system you choose to run. We recommend at least **8 GB** of memory, preferably 16 GB.

-------
Storage
-------

.. COMMENTED OUT FIXME: To bring the system up, we recommend at least **50 GB** of total disk space. In production, the storage requirements will vary greatly depending on the scope of the preservation project, from tens of gigabytes to hundreds of terabytes of preserved content.

LOCKSS makes use of several storage areas.  During configuration, the administrator must specify the location of these storage areas by supplying one or more directory paths. The default is to put all storage under a single directory, but different types of storage have different size and performance requirements and on a large system, if different types of storage are available it may be advantageous to place the storage areas on different devices:

*  **Content data storage:** This is where all the preserved content is stored, along with an index and several databases [#fn1]_. Many LOCKSS systems preserve a large amount of content and it has become common to use network-attached storage for this. LOCKSS' audit activities result in nearly continuous reading of content from storage; this may impact the storage server's performance, and a busy or non-performant storage server may impact LOCKSS' performance. For the repository service, multiple storage areas may be specified, and more can be added later.

   The amount of space required depends on the amount of content that will be preserved. The content is efficiently stored in large, compressed WARC files. Unlike LOCKSS 1.x, inode usage is very low.

*  **Log data storage:** Service logs will be written to subdirectories of this path. There is usually no reason to enter a different path unless you have specific logging requirements.

*  **Temporary data storage:** The LOCKSS software makes heavy use of temporary storage, and we recommend that temporary directories be placed on a filesystem with relatively low latency. If the content storage directories are on network storage (for example NFS), system performance may be improved by using a local directory.

   .. caution::

      Depending on the characteristics of the preservation activities undertaken by the system, in some circumstances content processing may require a substantial amount of temporary space, up to tens of gigabytes. Do not use a RAM-based ``tmpfs`` volume, or a directory in a space-constrained partition, for temporary data storage.

----

.. admonition:: What's the Minimum for Experimentation?

   To review the installation instructions and test the installation of K3s in various operating systems, we routinely install and bring up minimal LOCKSS 2.0-alpha4 systems, with no metadata services or Web replay engines, and with empty embedded Postgres and Solr databases, in Vagrant virtual machines with Virtualbox using 2 CPU cores and 3 GB of memory. These minimal VMs would not support a production load, but it can be a useful tool to try out the installation instructions or evaluate the system.

----

.. rubric:: Footnotes

.. [#fn1]

   Unless using external Solr and/or PostgreSQL servers.
