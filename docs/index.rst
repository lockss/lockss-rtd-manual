.. image:: /images/lockss-2.0-alpha2_200.png
   :alt: LOCKSS 2.0-alpha2 logo
   :align: right

====================
LOCKSS System Manual
====================

*Released: 2020-02-06. Last modified: 2021-04-12.*

**Welcome to the LOCKSS 2.0-alpha2 System Manual.**

-----------
What's New?
-----------

*  Ability to use external PostgreSQL or Solr databases run locally or institutionally, rather than the included PostgreSQL and Solr databases.

*  Many performance improvements in the repository, including paginated iteration and artifact caching.

*  Upgraded the included Solr database from 6.6.5 to 7.2.1, and added tools to upgrade Solr across versions and schemas.

*  REST services authenticate, and REST clients and the Pywb web replay engine provide credentials.

*  Numerous bug fixes and performance improvements, and enhancements to the UI, installer, tests, documentation, and more.

-------------
Prerequisites
-------------

In order to install and test the LOCKSS 2.0-alpha2 system, you will need:

*  64-bit **Linux** host (physical or virtual) with 4 cores and 8 GB of memory

*  **Docker** running in Swarm mode and with the Local-Persist volume plugin

*  **Git** to download the `lockss-installer` project from GitHub

See :doc:`installing/prerequisites` for more details.

-------
Upgrade
-------

In order to upgrade a LOCKSS 2.0-alpha1 system to LOCKSS 2.0-alpha2, you no longer need the Pystache Python module, but you will need to have **Java 8** on the host machine to run the Solr upgrade tool [#fn1]_ .

See :doc:`upgrading` for more details.

----------
Contact Us
----------

Please contact us for questions, feedback and bug reports. Open a ticket by sending e-mail to ``lockss-support (at) lockss (dot) org``. Your contribution toward the final LOCKSS 2.0 release is very important to us and greatly appreciated by the community.

--------
Versions
--------

The LOCKSS 2.0-alpha2 system consists of a configurable set of the following components:

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.0.3.0

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.0.9.0

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.0.2.0

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.0.1.0

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.0.1.0

*  `PostgreSQL <https://www.postgresql.org/>`_ version 9.6.12

*  `Apache Solr <https://lucene.apache.org/solr/>`_ version 7.2.1

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.2.20190410

--------------------------
Frequently Asked Questions
--------------------------

I have an existing classic LOCKSS system (version 1.x). Can I upgrade to LOCKSS 2.0-alpha2?
   The LOCKSS 2.0-alpha2 release is a technology preview which we are excited to share with the community for testing purposes. It is not yet possible to convert from a classic LOCKSS system (version 1.74.7) to a LOCKSS 2.0 system. To help us advance toward the final LOCKSS 2.0 release, please consider installing and running the LOCKSS 2.0-alpha2 release on a test machine and `providing us with your feedback <Contact Us>`_.

I have a LOCKSS system running 2.0-alpha1. Can I upgrade to LOCKSS 2.0-alpha2?
   Yes. You are welcome to wipe your testing data from LOCKSS 2.0-alpha1 and start from scratch, but there is an `upgrade path <Upgrade>`_ from LOCKSS 2.0-alpha1.

Can I use my own PostgreSQL database?
   Yes, in the LOCKSS 2.0-alpha2 system you can run the included PostgreSQL database, or configure it to use your local or institutional PostgreSQL database.

Can I use my own Solr database?
   Yes, likewise, the LOCKSS 2.0-alpha2 system can run an included Solr database, but you can can also configure it to use your local or institutional Solr database.

Can I replay Web content with my own Pywb instance?
   Yes, you can configure your own Pywb instance to connect directly to the LOCKSS Repository Service, or you can use the included Pywb instance, or you might choose not to run Pywb at all.

Can I replay Web content with my own OpenWayback instance?
   The LOCKSS 2.0-alpha2 system does not run an embedded OpenWayback instance yet, but it is possible to configure your own OpenWayback instance to connect directly to the LOCKSS Repository Service. `Contact us <Contact Us>`_ for instructions.

----

.. rubric:: Footnotes

.. [#fn1] This dependency on Java is temporary for 2.0-alpha2. It is necessary to run the Solr upgrader tool. In 2.0-alpha3, the process will be packaged in such a way that it does not depend on Java on the host machine.

.. toctree::
   :caption: LOCKSS System Manual
   :maxdepth: 1
   :hidden:
   :numbered:

   installing/index
   upgrading
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
