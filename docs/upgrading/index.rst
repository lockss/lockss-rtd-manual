.. danger::

   **This entire section is not yet updated for LOCKSS 2.0-beta2.** This is just the text from LOCKSS 2.0-beta1. *FIXME*

================
Upgrading LOCKSS
================

This chapter describes how to upgrade an existing LOCKSS 2.0 system from LOCKSS 2.0-alpha5, LOCKSS 2.0-alpha6, LOCKSS 2.0-alpha7, and earlier versions of LOCKSS |LATEST_MINOR| (LOCKSS 2.0.81-beta1, LOCKSS 2.0.82-beta1, LOCKSS 2.0.83-beta1), to LOCKSS |LATEST_PATCH|, the latest version of LOCKSS |LATEST_MINOR|.

.. tip::

   If you are installing the LOCKSS 2.x system for the first time, please see the installation instructions in the next chapter (:doc:`/installing/index`) instead.

.. note::

   Commands in this chapter are run as the ``lockss`` user [#fnlockss]_.

.. tip::

   Before you begin the upgrade, we recommend you first bring your operating system up to date by applying security updates and upgrading installed packages. Ask your system administrator or see :doc:`/sysadmin/os-updates` in the appendix.

.. only:: html and not singlehtml

   .. contents:: Chapter Table of Contents
      :local:
      :backlinks: none
      :depth: 1

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

As the ``lockss`` user [#fnlockss]_, run this Curl or Wget command [#fnfetcher]_:

.. tab-set::

   .. tab-item:: Curl
      :sync: curl

      .. code-block:: shell

         curl -sSfL https://lockss.org/downloader | sh -s -

   .. tab-item:: Wget
      :sync: wget

      .. code-block:: shell

         wget -qO- https://lockss.org/downloader | sh -s -

This will download and invoke the LOCKSS Downloader, which in turn will install the latest version of the LOCKSS Installer into the :ref:`Default LOCKSS Installer Directory` (:file:`{$HOME}/lockss-installer`). If you are using a custom LOCKSS Installer Directory :samp:`{DIR}`, remember to add :samp:`--download-dir={DIR}` to the end of the command; see :ref:`Running the LOCKSS Downloader` for details.

----------------------
Run the Upgrade Script
----------------------

If you are upgrading from a version prior to alpha7, the next step will update PostgreSQL from 9.6.12 to 14.7. In addition, if updating from 2.0-alpha5, the archived content will then be reindexed. Either of these operations, may take some time. As the ``lockss`` user, run the following command in the :ref:`LOCKSS Installer Directory`:

.. code-block:: shell

   scripts/upgrades/upgrade-to-beta1

.. hint::

   .. COMMENT PREVIOUSVERSION

   .. COMMENT LATESTVERSION

   If you have collected a substantial amount of content in the alpha system this may take a prohibitively long time. If you do not need that content, you can delete it and save time; see :doc:`/sysadmin/resetting`.

---------------------------
Re-run the Configure Script
---------------------------

Re-run the configuration script by running the command below and follow the instructions in :doc:`/configuring` to ensure all existing configuration parameters are still correct and to configure any new parameters:

.. code-block:: shell

   scripts/configure-lockss

If you do not need to review the existing configuration values, run this command instead:

.. code-block:: shell

   scripts/configure-lockss --replay

The ``--replay`` (or equivalently ``-r``) option will re-use all previously-entered configuration values, and only ask questions for new prompts added since the previous release.

---------------------------
Start LOCKSS |LATEST_MINOR|
---------------------------

You are now ready to start the LOCKSS system. Run this command as the ``lockss`` user [#fnlockss]_:

.. code-block:: shell

   scripts/start-lockss

----

.. rubric:: Footnotes

.. [#fnlockss]

   See :doc:`/sysadmin/lockss`.

.. [#fnfetcher]

   Most typical Linux systems have at least one of `Curl <https://curl.se/>`_ or `Wget <https://www.gnu.org/software/wget/>`_ installed by default. You can check by typing ``curl --version`` or ``wget --version`` and seeing which ones do not output an error message. See :doc:`/sysadmin/curl` or :doc:`/sysadmin/wget` for installation instructions.
