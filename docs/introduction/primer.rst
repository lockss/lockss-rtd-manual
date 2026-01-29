=============
LOCKSS Primer
=============

.. only:: html and not singlehtml

   .. sidebar::

      .. contents:: Section Table of Contents
         :local:
         :depth: 1
         :backlinks: none

This section offers a high-level introduction to the LOCKSS system, particularly LOCKSS 2.x.

---------------
What Is LOCKSS?
---------------

The **LOCKSS system** is a mature, open source, distributed digital preservation software system developed by the `LOCKSS Program <https://www.lockss.org/>`_ at `Stanford University Libraries <https://library.stanford.edu/>`_.

At the core of the LOCKSS system is **LCAP**, the LOCKSS Content Audit Protocol (originally the Library Content Audit Protocol), a sophisticated cryptographic audit and repair protocol that enables peer-to-peer networks called **LOCKSS networks** to preserve data together, with strong defense guarantees against digital preservation threats.

The LOCKSS system also includes components, tools and features to support diverse digital preservation activities:

*  A Web crawling framework, including the mature, extensible Classic LOCKSS Crawler;

*  A metadata extraction and retrieval framework, including DOI and OpenURL resolution;

*  Web replay engines, including LOCKSS ServeContent, Pywb, and OpenWayback;

*  A plugin system to apply the LOCKSS system's numerous configurable, extensible, and customizable behaviors to the particulars of a preservation target.

--------------------------
What Is New in LOCKSS 2.x?
--------------------------

LOCKSS 2.x stems from the LAAWS (LOCKSS Architected As Web Services) initiative, an ambitious modernization project that included rewriting LOCKSS 1.x from a monolithic daemon into a suite of containerized components with REST APIs, funded in part by a grant from the `Andrew W. Mellon Foundation <https://mellon.org/>`_.

Although LOCKSS 2.x is structurally different from LOCKSS 1.x, the audit and repair protocol remains the same (so LOCKSS networks can have a mixture of LOCKSS 1.x and 2.x nodes), and the plugin system is backward-compatible (so LOCKSS network operators can enjoy operational continuity during the transitional period).

LOCKSS 2.x offers an array of improvements compared to LOCKSS 1.x:

*  **Containerized architecture**. The functionality of LOCKSS 2.x is split into containerized components orchestrated by Kubernetes. Advantages over LOCKSS 1.x include:

   *  **Right-sized functionality**. You can pick and choose which :doc:`functional components <components>` you operate as part of your LOCKSS stack, skipping functionality not needed for your particular application. For example, many applications do not make use of metadata extraction or Web replay, and some applications do not make use of the Web crawling infrastructure to speak of, so you could leaves these components out of your configured stack if applicable.

   *  **Diverse Linux operating systems**. LOCKSS 2.x runs on the `K3s <https://k3s.io/>`_ Kubernetes distribution, which can be installed on diverse Linux :doc:`/appendix/os` fitting your organizational IT infrastructure. Previously, LOCKSS 1.x was restricted to RHEL-compatible Linux operating systems.

*  **Storage performance and scalability**: LOCKSS 2.x has a revamped storage backend. Advantages over LOCKSS 1.x include:

   *  **WARC-based storage format.** LOCKSS 2.x  aggregates preserved content into WARC files [#fn-warc]_, resulting in far fewer on-disk files, compression, and the ability for preserved content that is Web-harvested to be interoperable with other WARC-compatible Web archiving tools.

   *  **Database-based state management.** LOCKSS 2.x stores the state of preserved content in a `PostgreSQL <https://www.postgresql.org/>`_ database, offering efficiency and scalability. Previously, LOCKSS 1.x stored state in flat files.

   *  **Better storage utilization.** The LOCKSS 2.x storage repository can be configured to span multiple content storage areas, but unlike in LOCKSS 1.x, each archival unit (preserved collection of objects) can utilize them all. Previously, an AU would be assigned to a given content storage area and grow only there, which could lead to lopsided storage utilization and required rebalancing AUs across content storage areas.

----

.. rubric:: Footnotes

.. [#fn-warc] This is an implementation detail; to be stored, content does not have to be Web-harvested nor to be submitted as WARC files originally.
