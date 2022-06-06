================================================
NOT YET RELEASED LOCKSS 2.0-beta1 System Manual
================================================

**Welcome to the NOT YET RELEASED LOCKSS 2.0-beta1 System Manual.**

| Released: NOT YET RELEASED
| Last modified: |today|

.. only:: html

   .. _release-notes:

   -----------
   What's New?
   -----------

   What's New in 2.0-beta1?
   ========================

   *  FIXME

   ------------
   Installation
   ------------

   In order to install and test the LOCKSS 2.0-beta1 system, you will need:

   *  64-bit **Linux** host (physical or virtual) with at least 4 CPU cores and 8 GB of memory, and adequate storage.

   *  Commonplace Linux system utilities like :program:`curl`/:program:`wget` and :program:`tar` to run the LOCKSS Downloader and the LOCKSS Installer.

   *  **K3s**, a lightweight Kubernetes environment (installed via the LOCKSS Installer).

   See :doc:`/introduction/prerequisites` and :doc:`/installing/index` for more details.

   -------
   Upgrade
   -------

   See :doc:`/upgrading/index` for upgrade instructions from 2.0-alpha5.

   ---------------------
   Questions and Answers
   ---------------------

   I have an existing classic LOCKSS system (version 1.x). Can I upgrade to LOCKSS 2.0-beta1?
      FIXME

      The LOCKSS 2.0-beta1 release is a technology preview which we are excited to share with the community for testing purposes. It is not yet possible to convert from a classic LOCKSS system (e.g. version 1.75.8) to a LOCKSS 2.0 system for production purposes.

      However, an upcoming version of the classic LOCKSS system will contain an experimental tool to test the migration of select archival units (AUs) from a production 1.x system to a test 2.x system.

      To help us advance toward the final LOCKSS 2.0 release, please consider installing and running the LOCKSS 2.0-beta1 release on a test machine and :ref:`providing us with your feedback <Contact Us>`.

   I have a LOCKSS system running 2.0-alpha5. Can I upgrade to LOCKSS 2.0-beta1?
      Yes. You are welcome to wipe your testing data from LOCKSS 2.0-alpha5 and start from scratch, but there is an :ref:`upgrade path <Upgrade>` from LOCKSS 2.0-alpha5.

   Can I use my own PostgreSQL database? Can I use my own Solr database?
      Yes, you can configure the system to use your institution's Postgres database and/or Solr database -- or you can simply let system run included ones locally.

   Can I replay Web content with my own Pywb instance? Can I replay Web content with my own OpenWayback instance?
      Yes, you can configure your own Pywb instance and/or OpenWayback instance to connect directly to the LOCKSS Repository Service -- or you can let the system run included ones locally, or you can choose not to run any Web replay engine at all.

   ----------
   Contact Us
   ----------

   Please contact us for questions, feedback and bug reports. Open a ticket by sending e-mail to :email:`lockss-support@lockss.org`. Your contribution toward the final LOCKSS 2.0 release is very important to us and greatly appreciated by the community.

.. toctree::
   :caption: NOT YET RELEASED LOCKSS 2.0-beta1 System Manual
   :hidden:
   :numbered:

   introduction/index
   upgrading/index
   installing/index
   configuring
   running
   using/index
   troubleshooting/index
   sysadmin/index
   appendix/index

.. only:: html

   .. toctree::
      :caption: Navigation
      :hidden:

      « LOCKSS Documentation Portal <https://lockss.readthedocs.io/>
      « LOCKSS Web Site <https://www.lockss.org/>
