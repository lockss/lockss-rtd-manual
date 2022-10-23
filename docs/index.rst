===============================
LOCKSS 2.0-alpha2 System Manual
===============================

| Latest release: 2.0.26-alpha2 (2020-02-26)
| First release: 2.0.21-alpha2 (2020-02-06)
| System manual last built: |today|

**Welcome to the LOCKSS 2.0-alpha2 System Manual.**

.. only:: html

   -----------
   What's New?
   -----------

   Solr 7.2.1, ability to use external Postgres and Solr databases, REST authentication, and more. See our :doc:`/appendix/release-notes` for details.

   -------------
   Prerequisites
   -------------

   In order to install and test the LOCKSS 2.0-alpha2 system, you will need:

   *  64-bit **Linux** host (physical or virtual) with 4 cores and 8 GB of memory

   *  **Docker** running in Swarm mode and with the **Local-Persist** volume plugin

   *  **Git** to download the ``lockss-installer`` project from GitHub

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

   --------------------------
   Frequently Asked Questions
   --------------------------

   I have an existing classic LOCKSS system (version 1.x). Can I upgrade to LOCKSS 2.0-alpha2?
      The LOCKSS 2.0-alpha2 release is a technology preview which we are excited to share with the community for testing purposes. It is not yet possible to convert from a classic LOCKSS system (version 1.74.7) to a LOCKSS 2.0 system. To help us advance toward the final LOCKSS 2.0 release, please consider installing and running the LOCKSS 2.0-alpha2 release on a test machine and :ref:`providing us with your feedback <Contact Us>`_.

   I have a LOCKSS system running 2.0-alpha1. Can I upgrade to LOCKSS 2.0-alpha2?
      Yes. You are welcome to wipe your testing data from LOCKSS 2.0-alpha1 and start from scratch, but there is an :ref:`upgrade path <Upgrade>`_ from LOCKSS 2.0-alpha1.

   Can I use my own PostgreSQL database?
      Yes, in the LOCKSS 2.0-alpha2 system you can run the included PostgreSQL database, or configure it to use your local or institutional PostgreSQL database.

   Can I use my own Solr database?
      Yes, likewise, the LOCKSS 2.0-alpha2 system can run an included Solr database, but you can can also configure it to use your local or institutional Solr database.

   Can I replay Web content with my own Pywb instance?
      Yes, you can configure your own Pywb instance to connect directly to the LOCKSS Repository Service, or you can use the included Pywb instance, or you might choose not to run Pywb at all.

   Can I replay Web content with my own OpenWayback instance?
      The LOCKSS 2.0-alpha2 system does not run an embedded OpenWayback instance yet, but it is possible to configure your own OpenWayback instance to connect directly to the LOCKSS Repository Service. :ref:`Contact us <Contact Us>`_ for instructions.

   ----

   .. rubric:: Footnotes

   .. [#fn1] This dependency on Java is temporary for 2.0-alpha2. It is necessary to run the Solr upgrader tool. In 2.0-alpha3, the process will be packaged in such a way that it does not depend on Java on the host machine.

.. toctree::
   :caption: LOCKSS 2.0-alpha2 System Manual
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
