===========================
Upgrading the LOCKSS System
===========================

.. note::

   This chapter describes how to upgrade an existing LOCKSS 2.0-alpha5, 2.0-alpha6, or 2.0.71-alpha7 system to |LATEST_MINOR|. If you are installing the LOCKSS 2.x system for the first time, please see the installation instructions in the next chapter:

   .. button-ref:: /installing/index
      :ref-type: doc
      :color: primary
      :outline:
      :align: center

.. tip::

   Before you begin the upgrade, we strongly recommend you first bring your operating system up to date by applying security updates and upgrading installed packages. Ask your system administrator or see :doc:`/sysadmin/os-updates` in the appendix.

.. note::

   Commands in this section are run as the ``lockss`` user  [#fnlockss]_.

.. COMMENT PREVIOUSVERSION

----------------------
Stop the LOCKSS System
----------------------

The first step is to stop the running LOCKSS system. Log in as the ``lockss`` user and run the following command in the :ref:`LOCKSS Installer Directory`:

.. code-block:: shell

   scripts/stop-lockss

You may verify all LOCKSS components have stopped by running the following command:

.. code-block:: shell

   k3s kubectl get deployments -n lockss

which should return:

.. code-block:: text

   No resources found in lockss namespace.

---------------------------
Update the LOCKSS Installer
---------------------------

As the ``lockss`` user [#fnlockss]_, run this Curl, Wget or HTTPie command [#fnfetcher]_:

.. tab-set::
   :class: sd-bg-light

   .. tab-item:: Curl
      :sync: curl

      .. code-block:: shell

         curl -sSfL https://lockss.org/downloader | sh -s -

   .. tab-item:: HTTPie
      :sync: httpie

      .. code-block:: shell

         http -qd https://lockss.org/downloader | sh -s -

   .. tab-item:: Wget
      :sync: wget

      .. code-block:: shell

         wget -qO- https://lockss.org/downloader | sh -s -

This will download and invoke the LOCKSS Downloader, which in turn will install the latest version of the LOCKSS Installer into the :ref:`Default LOCKSS Installer Directory` (:file:`{$HOME}/lockss-installer`). If you are using a custom LOCKSS Installer Directory :samp:`{DIR}`, remember to add :samp:`--download-dir={DIR}` to the end of the command; see :ref:`Running the LOCKSS Downloader` for details.

----------------------
Run the Upgrade Script
----------------------

The next step will update PostgreSQL from 9.6.12 to 14.7 if applicable. In addition, if updating from 2.0-alpha5, the archived content will then be reindexed. As the ``lockss`` user, run the following command in the :ref:`LOCKSS Installer Directory`:

.. code-block:: shell

   scripts/upgrades/upgrade-to-alpha7

.. hint::

   .. COMMENT PREVIOUSVERSION

   .. COMMENT LATESTVERSION

  If it takes more than a few seconds for ``upgrade-to-alpha7`` above to run, the reindexing of all previously archived content which occurs the first time you start 2.0-alpha7 after upgrading from 2.0-alpha5 may take prohibitively long. This performance issue will be addressed in a later release. If you do not need the previously stored content during alpha testing, you could delete it and skip this reindexing step; see :doc:`/sysadmin/resetting`.

---------------------------
Re-run the Configure Script
---------------------------

Re-run the configuration script by running the command below and follow the instructions in :doc:`/configuring` to ensure all existing configuration parameters are still correct and to configure any new parameters:

.. code-block:: shell

   scripts/configure-lockss -r

The ``-r`` ("replay") option will re-use all previously-entered configuration values, and only ask questions for new prompts added since the previous release.

---------------------------
Start LOCKSS |LATEST_MINOR|
---------------------------

You are now ready to start the LOCKSS system.

*  If you were upgrading from LOCKSS 2.0.71-alpha7, run this command:

   .. code-block:: shell

      scripts/start-lockss -u

*  If you were upgrading from LOCKSS 2.0-alpha5 or LOCKSS 2.0-alpha6, run this command:

   .. code-block:: shell

      scripts/start-lockss

   .. hint::

      .. COMMENT PREVIOUSVERSION

      .. COMMENT LATESTVERSION

      If it takes more than a few seconds for ``upgrade-to-alpha7`` above to run, the reindexing of all previously archived content which occurs the first time you start 2.0-alpha7 after upgrading from 2.0-alpha5 may take prohibitively long. This performance issue will be addressed in a later release. If you do not need the previously stored content during alpha testing, you could delete it and skip this reindexing step; see :doc:`/sysadmin/resetting`.

----

.. rubric:: Footnotes

.. [#fnlockss]

   See :doc:`/sysadmin/lockss`.

.. [#fnfetcher]

   Most typical Linux systems have at least one of `Curl <https://curl.se/>`_, `Wget <https://www.gnu.org/software/wget/>`_ or `HTTPie <https://httpie.io/>`_ installed by default. You can check by typing ``curl --version``, ``wget --version`` or ``http --version``, and seeing which ones do not output an error message. See :doc:`/sysadmin/curl`, :doc:`/sysadmin/wget` or :doc:`/sysadmin/httpie` for installation instructions.
