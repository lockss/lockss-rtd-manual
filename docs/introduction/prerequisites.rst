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

To bring the system up, we recommend at least **50 GB** of disk space. In production, the storage requirements will vary greatly depending on the scope of the preservation project, from tens of gigabytes to hundreds of terabytes of preserved content.

*FIXME talk about local/network storage*

.. admonition:: What's the Minimum for Experimentation?

   We have been able to install and bring up minimal LOCKSS 2.0-alpha4 systems (with no metadata services or Web replay engines, and with empty embedded Postgres and Solr databases) in Vagrant virtual machines (with Virtualbox), with 2 CPU cores and 2 GB of memory allocated. But the VMs are swapping heavily and would not support much computational load. Still, it can be a useful tool to try out the installation instructions or evaluate the system.
