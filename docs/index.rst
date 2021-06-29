.. image:: /images/lockss-2.0-alpha4_200.png
   :alt: LOCKSS 2.0-alpha4 logo
   :align: right

===============================
LOCKSS 2.0-alpha4 System Manual
===============================

**Welcome to the LOCKSS 2.0-alpha4 System Manual.**

| Released: 2021-06-28.
| Last modified: |today|.

.. only:: html

   .. _release-notes:

   -----------
   What's New?
   -----------

   *  Containers are now orchestrated by **K3s**, a lightweight Kubernetes distribution by Kubernetes vendor `Rancher <https://rancher.com/>`_. K3s is compatible with most Linux flavors and comes with a convenient multi-OS installer.

   *  Content is now stored in compressed WARC files by default.

   *  Numerous bug fixes and enhancements in the repository service and underlying componentry, delivering more reliability and performance in error handling, scalability, and content replay.

   *  Many security enhancements, including support for :program:`firewalld` and :program:`ufw`, containers not running as ``root`` internally, the ``lockss`` user no longer needing :program:`sudo` privileges, Solr authentication, and LCAP SSL support with TLSv1.2 by default.

   *  Web user interface enhancements, including LCAP SSL key generation and support for the Kubernetes dashboard.

   ------------
   Installation
   ------------

   In order to install and test the LOCKSS 2.0-alpha4 system, you will need:

   *  64-bit **Linux** host (physical or virtual) with at least 4 CPU cores and 8 GB of memory, and adequate storage.

   *  **Git**, to download the LOCKSS Installer from GitHub.

   *  **K3s**, a lightweight Kubernetes environment installed via the LOCKSS Installer.

   See :doc:`/introduction/prerequisites` and :doc:`/installing/index` for more details.

   -------
   Upgrade
   -------

   If you were running LOCKSS 2.0-alpha3, you no longer need MicroK8s or Snap. See :doc:`upgrading/index` for more details.

   ---------------------
   Questions and Answers
   ---------------------

   I have an existing classic LOCKSS system (version 1.x). Can I upgrade to LOCKSS 2.0-alpha4?
      The LOCKSS 2.0-alpha4 release is a technology preview which we are excited to share with the community for testing purposes. It is not yet possible to convert from a classic LOCKSS system (e.g. version 1.75.5) to a LOCKSS 2.0 system. To help us advance toward the final LOCKSS 2.0 release, please consider installing and running the LOCKSS 2.0-alpha4 release on a test machine and :ref:`providing us with your feedback <Contact Us>`.

   I have a LOCKSS system running 2.0-alpha3. Can I upgrade to LOCKSS 2.0-alpha4?
      Yes. You are welcome to wipe your testing data from LOCKSS 2.0-alpha3 and start from scratch, but there is an :ref:`upgrade path <Upgrade>` from LOCKSS 2.0-alpha3.

   Can I use my own PostgreSQL database? Can I use my own Solr database?
      Yes, you can configure the system to use your institution's Postgres database and/or Solr database -- or you can simply let system run included ones locally.

   Can I replay Web content with my own Pywb instance? Can I replay Web content with my own OpenWayback instance?
      Yes, you can configure your own Pywb instance and/or OpenWayback instance to connect directly to the LOCKSS Repository Service -- or you can let the system run included ones locally, or you can choose not to run any Web replay engine at all.

   ----------
   Contact Us
   ----------

   Please contact us for questions, feedback and bug reports. Open a ticket by sending e-mail to ``lockss-support (at) lockss (dot) org``. Your contribution toward the final LOCKSS 2.0 release is very important to us and greatly appreciated by the community.

.. toctree::
   :caption: LOCKSS 2.0-alpha4 System Manual
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
