==========================
Frequently Asked Questions
==========================

This section answers some common questions about the LOCKSS system.

I have an existing classic LOCKSS system (version 1.x). Can I migrate to LOCKSS |LATEST_MINOR|?

   It is possible to migrate from LOCKSS 1.78 to LOCKSS |LATEST_MINOR| now, except for LOCKSS nodes participating in the Global LOCKSS Network (GLN), in which case we strongly recommend waiting until a subsequent beta release of LOCKSS 2.x for that node. We invite you to read the :doc:`lockss:migration/index` and give us feedback to help improve the documentation.

I have a LOCKSS system running |PREVIOUS_MINOR|. Can I upgrade to LOCKSS |LATEST_MINOR|?
   Yes. You are welcome to wipe your testing data from LOCKSS 2.0-alpha6 and start from scratch, but there is an :doc:`upgrade path </upgrading/index>` from LOCKSS 2.0-alpha6.

Can I use my own PostgreSQL database? Can I use my own Solr database?
   Yes, you can configure the system to use your institution's Postgres database and/or Solr database -- or you can simply let system run included ones locally.

Can I replay Web content with my own Pywb instance? Can I replay Web content with my own OpenWayback instance?
   Yes, you can configure your own Pywb instance and/or OpenWayback instance to connect directly to the LOCKSS Repository Service -- or you can let the system run included ones locally, or you can choose not to run any Web replay engine at all.
