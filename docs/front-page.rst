.. grid:: 1 1 2 2

   .. grid-item::

      .. card:: Latest Release
         :text-align: center

         .. COMMENT LATESTVERSION

         .. COMMENT RELEASEDATE

         2.0.60-alpha6 (NOT YET RELEASED)

         .. button-ref:: appendix/release-notes
            :ref-type: doc
            :color: info
            :expand:

         .. button-ref:: troubleshooting/support
            :ref-type: doc
            :color: info
            :expand:

         .. COMMENT add :outline: if there are no advisories for that version yet, remove it when there are:

         .. button-ref:: appendix/security
            :ref-type: doc
            :color: danger
            :expand:
            :outline:

   .. grid-item::

      .. card:: How To...
         :text-align: center

         .. button-ref:: upgrading/index
            :ref-type: doc
            :color: primary
            :expand:

            Upgrade

         .. button-ref:: installing/index
            :ref-type: doc
            :color: primary
            :expand:

            Install

         .. button-ref:: configuring
            :ref-type: doc
            :color: primary
            :expand:

            Configure

         .. button-ref:: running
            :ref-type: doc
            :color: primary
            :expand:

            Run

         .. button-ref:: using/index
            :ref-type: doc
            :color: primary
            :expand:

            Use

         .. button-ref:: troubleshooting/index
            :ref-type: doc
            :color: primary
            :expand:

            Troubleshoot

.. COMMENT LATESTVERSION

-------------------------
What's New in 2.0-alpha6?
-------------------------

FIXME

See the full :doc:`/appendix/release-notes`.

------------
Installation
------------

.. COMMENT LATESTVERSION

In order to install and test the LOCKSS 2.0-alpha6 system, you will need a 64-bit **Linux** host (physical or virtual) with at least 4 CPU cores and 8 GB of memory; adequate storage for your preservation activities; commonplace Linux system utilities like :program:`curl`/:program:`wget` and :program:`tar` to run the LOCKSS Downloader and the LOCKSS Installer; and **K3s**, a lightweight Kubernetes environment installed via the LOCKSS Installer.

See :doc:`/introduction/prerequisites` and :doc:`/installing/index` for more details.

-------
Upgrade
-------

.. COMMENT PREVIOUSVERSION

See :doc:`/upgrading/index` for upgrade instructions from 2.0-alpha5.

---------------------
Questions and Answers
---------------------

.. COMMENT LATESTVERSION

I have an existing classic LOCKSS system (version 1.x). Can I upgrade to LOCKSS 2.0-alpha6?
   FIXME

   .. COMMENT LATESTVERSION

   The LOCKSS 2.0-alpha6 release is a technology preview which we are excited to share with the community for testing purposes. It is not yet possible to convert from a classic LOCKSS system (e.g. version 1.75.8) to a LOCKSS 2.0 system for *production* purposes.

   However, version 1.76 of the classic LOCKSS system contains a prototype tool to test the migration of archival units (AUs) from a production 1.x system to a *test* 2.x system, for *testing* purposes.

   .. COMMENT LATESTVERSION

   To help us advance toward the final LOCKSS 2.0 release, please consider installing and running the LOCKSS 2.0-alpha6 release on a test machine and :ref:`providing us with your feedback <Contact Us>`.

.. COMMENT PREVIOUSVERSION

.. COMMENT LATESTVERSION

I have a LOCKSS system running 2.0-alpha5. Can I upgrade to LOCKSS 2.0-alpha6?
   Yes. You are welcome to wipe your testing data from LOCKSS 2.0-alpha6 and start from scratch, but there is an :ref:`upgrade path <Upgrade>` from LOCKSS 2.0-alpha5.

Can I use my own PostgreSQL database? Can I use my own Solr database?
   Yes, you can configure the system to use your institution's Postgres database and/or Solr database -- or you can simply let system run included ones locally.

Can I replay Web content with my own Pywb instance? Can I replay Web content with my own OpenWayback instance?
   Yes, you can configure your own Pywb instance and/or OpenWayback instance to connect directly to the LOCKSS Repository Service -- or you can let the system run included ones locally, or you can choose not to run any Web replay engine at all.

----------
Contact Us
----------

Please contact us for questions, feedback and bug reports. Open a ticket by sending e-mail to :email:`lockss-support@lockss.org`. Your contribution toward the final LOCKSS 2.0 release is very important to us and greatly appreciated by the community.

----

System manual last built: |today|
