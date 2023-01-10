==========================
Frequently Asked Questions
==========================

This section answers some common questions about the LOCKSS system.

.. COMMENT LATESTVERSION

I have an existing classic LOCKSS system (version 1.x). Can I upgrade to LOCKSS 2.0-alpha6?
   .. COMMENT LATESTVERSION

   The LOCKSS 2.0-alpha6 release is a technology preview which we are excited to share with the community for testing purposes. It is not yet possible to convert from a classic LOCKSS system (e.g. version 1.76.4) to a LOCKSS 2.0 system for *production* purposes.

   However, version 1.76 of the classic LOCKSS system contains a prototype tool to test the migration of archival units (AUs) from a production 1.76 system to a *test* 2.0-alpha6 system, for *testing* purposes. See https://github.com/lockss/community/wiki/Migration-Tool.

   .. COMMENT LATESTVERSION

   .. COMMENT FIXME does this contact us link go anywhere anymore?

   To help us advance toward the final LOCKSS 2.0 release, please consider installing and running the LOCKSS 2.0-alpha6 release on a test machine and :ref:`providing us with your feedback <Contact Us>`.

.. COMMENT PREVIOUSVERSION

.. COMMENT LATESTVERSION

I have a LOCKSS system running 2.0-alpha5. Can I upgrade to LOCKSS 2.0-alpha6?
   Yes. You are welcome to wipe your testing data from LOCKSS 2.0-alpha6 and start from scratch, but there is an :doc:`upgrade path </upgrading/index>` from LOCKSS 2.0-alpha5.

Can I use my own PostgreSQL database? Can I use my own Solr database?
   Yes, you can configure the system to use your institution's Postgres database and/or Solr database -- or you can simply let system run included ones locally.

Can I replay Web content with my own Pywb instance? Can I replay Web content with my own OpenWayback instance?
   Yes, you can configure your own Pywb instance and/or OpenWayback instance to connect directly to the LOCKSS Repository Service -- or you can let the system run included ones locally, or you can choose not to run any Web replay engine at all.
