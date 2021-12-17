.. image:: /images/lockss-2.0-alpha5_200.png
   :alt: LOCKSS 2.0-alpha5 logo
   :align: right

.. comment FIX-AFTER-RELEASE

==============================================
LOCKSS 2.0-alpha5 (NOT RELEASED) System Manual
==============================================

.. comment FIX-AFTER-RELEASE

.. warning::

   **You are viewing a work in progress for a future version of the LOCKSS System.**

   .. only:: html

      `Click here to go to the latest released version </projects/manual/en/latest>`_.

.. comment FIX-AFTER-RELEASE

**Welcome to the LOCKSS 2.0-alpha5 (NOT RELEASED) System Manual.**

.. comment FIX-AFTER-RELEASE

| Released: 2021-XX-XX.
| Last modified: |today|.

.. only:: html

   .. _release-notes:

   -----------
   What's New?
   -----------

   *  Numerous bug fixes and substantial performance improvements in the LOCKSS Repository Service, in support of reliability, scalability, and LOCKSS 1.x to 2.x migration.

   *  Improved LOCKSS Installer distributed without requiring Git, rolling up most individual installation steps into a single script.

   *  Upgrade from Solr 7.2.1 to 8.9.0.

   *  Revamped HTTP error response handling, including new HTTP response/error categories and custom handling of categories in plugins.

   *  Added support for communicating with APIs via POST requests during crawls.

   *  All system components and the custom Solr and OpenWayback Docker containers included in the system now contain only the latest version of Log4j (2.16.0), which is not vulnerable to CVE-2021-44228 ("Log4Shell"), CVE-2021-45046 and CVE-2021-4104.

   ------------
   Installation
   ------------

   In order to install and test the LOCKSS 2.0-alpha5 system, you will need:

   *  64-bit **Linux** host (physical or virtual) with at least 4 CPU cores and 8 GB of memory, and adequate storage.

   *  Commonplace Linux system utilities like :program:`curl`/:program:`wget` and :program:`tar` to run the LOCKSS Downloader and the LOCKSS Installer.

   *  **K3s**, a lightweight Kubernetes environment (installed via the LOCKSS Installer).

   See :doc:`/introduction/prerequisites` and :doc:`/installing/index` for more details.

   -------
   Upgrade
   -------

   If you were running LOCKSS 2.0-alpha4, Git is no longer required. See :doc:`/upgrading/index` for upgrade instructions.

   .. important::

      The LOCKSS 2.0-alpha4 system, and the Solr and OpenWayback containers it includes, are affected by CVE-2021-44228 ("Log4Shell"), CVE-2021-45046 and CVE-2021-4104. Please `see the LOCKSS 2.0-alpha4 security advisory </projects/manual/en/2.0-alpha4/appendix/security>`_ and :doc:`upgrade to LOCKSS 2.0-alpha5 </upgrading/index>`.

   ---------------------
   Questions and Answers
   ---------------------

   Is LOCKSS 2.0-alpha5 vulnerable to CVE-2021-44228 ("Log4Shell")?
      No. The LOCKSS 2.0-alpha5 system, and the custom Solr 8.9.0 and OpenWayback 2.4.0 Docker containers it ships with, contain the only the latest version of Log4j (2.16.0), which is not vulnerable to CVE-2021-44228 ("Log4Shell"), CVE-2021-45046 and CVE-2021-4104. See :doc:`/appendix/security`.

   I have an existing classic LOCKSS system (version 1.x). Can I upgrade to LOCKSS 2.0-alpha5?
      The LOCKSS 2.0-alpha5 release is a technology preview which we are excited to share with the community for testing purposes. It is not yet possible to convert from a classic LOCKSS system (e.g. version 1.75.8) to a LOCKSS 2.0 system for production purposes.

      However, an upcoming version of the classic LOCKSS system will contain an experimental tool to test the migration of select archival units (AUs) from a production 1.x system to a test 2.x system.

      To help us advance toward the final LOCKSS 2.0 release, please consider installing and running the LOCKSS 2.0-alpha5 release on a test machine and :ref:`providing us with your feedback <Contact Us>`.

   I have a LOCKSS system running 2.0-alpha4. Can I upgrade to LOCKSS 2.0-alpha5?
      Yes. You are welcome to wipe your testing data from LOCKSS 2.0-alpha4 and start from scratch, but there is an :ref:`upgrade path <Upgrade>` from LOCKSS 2.0-alpha4.

   Can I use my own PostgreSQL database? Can I use my own Solr database?
      Yes, you can configure the system to use your institution's Postgres database and/or Solr database -- or you can simply let system run included ones locally.

      Please note that as of this writing, only Solr 8.11.1 is not vulnerable to CVE-2021-44228 ("Log4Shell") and CVE-2021-45046. If you choose to run an external Solr database, you are responsible for ensuring it is not vulnerable.

   Can I replay Web content with my own Pywb instance? Can I replay Web content with my own OpenWayback instance?
      Yes, you can configure your own Pywb instance and/or OpenWayback instance to connect directly to the LOCKSS Repository Service -- or you can let the system run included ones locally, or you can choose not to run any Web replay engine at all.

      Please note that as of this writing, OpenWayback is vulnerable to CVE-2021-44228 ("Log4Shell") and CVE-2021-45046. If you choose to run an external OpenWayback replay engine, you are responsible for ensuring it is not vulnerable.

   ----------
   Contact Us
   ----------

   Please contact us for questions, feedback and bug reports. Open a ticket by sending e-mail to ``lockss-support (at) lockss (dot) org``. Your contribution toward the final LOCKSS 2.0 release is very important to us and greatly appreciated by the community.

.. toctree::
   :caption: LOCKSS 2.0-alpha5 System Manual
   :maxdepth: 4
   :hidden:
   :numbered:

   introduction/index
   upgrading/index
   installing/index
   configuring
   running
   using/index
   troubleshooting/index
   appendix/index

.. only:: html

   .. toctree::
      :caption: LOCKSS Documentation Portal
      :maxdepth: 1
      :hidden:

      Home <https://lockss.readthedocs.io/>
      LOCKSS System Manual <https://lockss.readthedocs.io/projects/manual/>
