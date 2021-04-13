.. image:: /images/lockss-2.0-alpha1_200.png
   :alt: LOCKSS 2.0-alpha1 logo
   :align: right

===============================
LOCKSS 2.0-alpha1 System Manual
===============================

*Released: 2019-05-13. Last modified: 2021-04-12.*

**Welcome to the LOCKSS 2.0-alpha1 System Manual.**

-----------
What's New?
-----------

The LOCKSS 2.0-alpha1 release features:

*  Storage in the **LOCKSS Repository Service**, on top of `Solr <https://lucene.apache.org/solr/>`_.

*  Node configuration and state management in the **LOCKSS Configuration Service**.

*  Content ingest with the LOCKSS Crawler.

*  LOCKSS polling and repair with the **LOCKSS Poller Service**.

*  Metadata extraction and query in the **LOCKSS Metadata Extraction Service** and **LOCKSS Metadata Service**, on top of a `Postgres <https://www.postgresql.org/>`_ database.

*  Web replay with LOCKSS ServeContent and `Pywb <https://github.com/webrecorder/pywb>`_, the state-of-the-art Web replay engine behind `Webrecorder <https://webrecorder.io/>`_.

--------------
Pre-Requisites
--------------

In order to install and test the LOCKSS 2.0-alpha1 system, you will need:

*  64-bit **Linux** host (physical or virtual) with 4 cores and 8 GB of memory

*  **Docker** running in Swarm mode and with the Local-Persist volume plugin

*  **Git** to download a small project from GitHub

*  The Setuptools and Pystache Python modules

----------
Contact Us
----------

Please contact us for questions, feedback and bug reports. Open a ticket by sending e-mail to ``lockss-support (at) lockss (dot) org``. Your contribution toward the final LOCKSS 2.0 release is very important to us and greatly appreciated by the community.

--------------------------
Frequently Asked Questions
--------------------------

I have an existing LOCKSS system (version 1.x). Can I upgrade to LOCKSS 2.0-alpha1?
   The LOCKSS 2.0-alpha1 release is a technology preview which we are excited to share with the community for testing purposes. It is not yet possible to convert from a classic LOCKSS system (version 1.74.7) to a LOCKSS 2.0 system. To help us advance toward the final LOCKSS 2.0 release, please consider installing and running the LOCKSS 2.0-alpha1 release and :ref:`providing us with your feedback <Contact Us>`.

Can I use my own Postgres database?
   The LOCKSS 2.0-alpha1 system runs its own Postgres database. The LOCKSS 2.0-alpha2 system will allow you to use your own Postgres database instead if you choose.

Can I use my own Solr database?
   The LOCKSS 2.0-alpha1 system comes with its own Solr database. In the LOCKSS 2.0-alpha2 system, you will be able to choose to use your own Solr database if you prefer.

Can I use the HDFS storage in my own Hadoop cluster?
   The LOCKSS 2.0-alpha1 system spins up its own HDFS storage. The LOCKSS 2.0-beta system will enable you to connect to your own HDFS storage over an unanthenticated HDFS port. If there is interest in connecting the LOCKSS system to HDFS storage over a port authenticated via Kerberos, the LOCKSS team will include it as part of its future development roadmap.

Can I replay Web content with my own Pywb instance?
   Yes, the LOCKSS 2.0-alpha1 system runs an embedded Pywb instance, but it is possible to configure your own Pywb instance to connect directly to the LOCKSS Repository Service. :ref:`Contact us <Contact Us>` for instructions. The LOCKSS 2.0-alpha2 release will enable you to skip the embedded Pywb instance entirely.

Can I replay Web content with my own OpenWayback instance?
   The LOCKSS 2.0-alpha1 system does not run an embedded OpenWayback instance, but it is possible to configure your own OpenWayback instance to connect directly to the LOCKSS Repository Service. :ref:`Contact us <Contact Us>` for instructions. (A future release will enable you to run an embedded OpenWayback instance if you choose.)

.. toctree::
   :caption: LOCKSS 2.0-alpha1 System Manual
   :maxdepth: 1
   :hidden:
   :numbered:

   installing/index
   configuring
   running
   using/index
   appendix/index

.. toctree::
   :caption: LOCKSS Documentation Portal
   :maxdepth: 1
   :hidden:

   Home <https://lockss.readthedocs.io/>
   LOCKSS System Manual <https://lockss.readthedocs.io/projects/manual/>
