.. image:: /images/lockss-2.0-alpha5_200.png
   :alt: LOCKSS 2.0-alpha5 logo
   :align: right

==============================================
LOCKSS 2.0-alpha5 (NOT RELEASED) System Manual
==============================================

.. warning::

   **You are viewing a work in progress for a future version of the LOCKSS System.**

   .. only:: html

      `Click here to go to the latest released version </projects/manual/en/latest>`_.

**Welcome to the LOCKSS 2.0-alpha5 (NOT RELEASED) System Manual.**

| Released: 2021-XX-XX.
| Last modified: |today|.

.. only:: html

   .. _release-notes:

   -----------
   What's New?
   -----------

   *  The LOCKSS Installer is now distributed from GitHub but without requiring :program:`git` and rolls up most individual installation steps into a single script.

   *  **FIXME**

   ------------
   Installation
   ------------

   **FIXME**

   In order to install and test the LOCKSS 2.0-alpha4 system, you will need:

   *  64-bit **Linux** host (physical or virtual) with at least 4 CPU cores and 8 GB of memory, and adequate storage.

   *  Commonplace Linux system utilities like :program:`curl`/:program:`wget` and :program:`tar` to download and run the LOCKSS Installer.

   *  **K3s**, a lightweight Kubernetes environment installed via the LOCKSS Installer.

   See :doc:`/introduction/prerequisites` and :doc:`/installing/index` for more details.

   -------
   Upgrade
   -------

   **FIXME**

   If you were running LOCKSS 2.0-alpha4, you no longer need Git. See :doc:`upgrading/index` for more details.

   ---------------------
   Questions and Answers
   ---------------------

   **FIXME**

   I have an existing classic LOCKSS system (version 1.x). Can I upgrade to LOCKSS 2.0-alpha5?
      **FIXME**

      The LOCKSS 2.0-alpha4 release is a technology preview which we are excited to share with the community for testing purposes. It is not yet possible to convert from a classic LOCKSS system (e.g. version 1.75.5) to a LOCKSS 2.0 system. To help us advance toward the final LOCKSS 2.0 release, please consider installing and running the LOCKSS 2.0-alpha4 release on a test machine and :ref:`providing us with your feedback <Contact Us>`.

   I have a LOCKSS system running 2.0-alpha4. Can I upgrade to LOCKSS 2.0-alpha5?
      Yes. You are welcome to wipe your testing data from LOCKSS 2.0-alpha4 and start from scratch, but there is an :ref:`upgrade path <Upgrade>` from LOCKSS 2.0-alpha4.

   Can I use my own PostgreSQL database? Can I use my own Solr database?
      Yes, you can configure the system to use your institution's Postgres database and/or Solr database -- or you can simply let system run included ones locally.

   Can I replay Web content with my own Pywb instance? Can I replay Web content with my own OpenWayback instance?
      Yes, you can configure your own Pywb instance and/or OpenWayback instance to connect directly to the LOCKSS Repository Service -- or you can let the system run included ones locally, or you can choose not to run any Web replay engine at all.

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
