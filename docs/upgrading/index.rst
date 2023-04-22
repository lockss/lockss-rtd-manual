======================================
Upgrading From LOCKSS |PREVIOUS_MINOR|
======================================

.. note::

   This chapter describes how to upgrade an existing LOCKSS |PREVIOUS_MINOR| system to |LATEST_MINOR|. If you are installing the LOCKSS 2.x system for the first time, please see the installation instructions in the next chapter:

   .. button-ref:: /installing/index
      :ref-type: doc
      :color: primary
      :outline:
      :align: center

.. tip::

   Before you begin the upgrade, we strongly recommend you first bring your operating system up to date by applying security updates and upgrading installed packages. Ask your system administrator or see :doc:`/sysadmin/os-updates` in the appendix.

.. COMMENT PREVIOUSVERSION

----------------------------
Stop LOCKSS |PREVIOUS_MINOR|
----------------------------

The first step is to stop the LOCKSS |PREVIOUS_MINOR| system. Log in as the ``lockss`` user and run the following command in the :ref:`LOCKSS Installer Directory` (by default :file:`{$HOME}/lockss-installer`, typically :file:`/home/lockss/lockss-installer`).

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

As of 2.0-alpha5, the official way to install and upgrade the LOCKSS Installer is using the LOCKSS Downloader, rather than cloning the LOCKSS Installer as a Git project. The instructions below detail the use of the LOCKSS Downloader. (Advanced
users may continue to use :program:`git` if they wish; please see :doc:`/appendix/git-downloader` for instructions.)

As the ``lockss`` user, run either this :program:`curl` command:

.. code-block:: shell

   curl -sSfL https://lockss.org/downloader | sh -s -

Or this :program:`wget` command:

.. code-block:: shell

   wget -qO- https://lockss.org/downloader | sh -s -

This will download and invoke the LOCKSS Downloader, which in turn will install the latest version of the LOCKSS Installer into the default LOCKSS Installer Directory (:file:`{$HOME}/lockss-installer`). If you are using a custom LOCKSS Installer Directory :samp:`{DIR}`, remember to use :samp:`--download-dir={DIR}`; see :ref:`Running the LOCKSS Downloader` for details.

----------------------
Run the Upgrade Script
----------------------

FIXME (this section is likely different for beta1)

The next step is to update archived content from the previous release version. As the ``lockss`` user, run the following command in the :ref:`LOCKSS Installer Directory`:

.. code-block:: shell

   scripts/upgrades/upgrade-to-alpha6

.. hint::

   .. COMMENT PREVIOUSVERSION

   .. COMMENT LATESTVERSION

   If it takes more than a few seconds for ``upgrade-to-alpha6`` above to run, the reindexing of all previously archived content which occurs the first time you start 2.0-alpha6 after upgrading from 2.0-alpha5 may take prohibitively long. This performance issue will be addressed in the next release. If you do not need the previously stored content during alpha testing, you could delete it and skip this reindexing step; see :doc:`/sysadmin/resetting`.

---------------------------
Re-run the Configure Script
---------------------------

Re-run the configuration script by running the command below and follow the instructions in :doc:`/configuring` to ensure all existing configuration parameters are still correct and to configure any new parameters:

.. code-block:: shell

   scripts/configure-lockss

-----------------------
Start LOCKSS 2.0-alpha6
-----------------------

Follow the instructions in :doc:`/running` to start your LOCKSS |LATEST_MINOR| instance:

.. code-block:: shell

   scripts/start-lockss

.. hint::

   .. COMMENT PREVIOUSVERSION

   .. COMMENT LATESTVERSION

    FIXME (this section is likely different for beta1)

   If it takes more than a few seconds for ``upgrade-to-alpha6`` above to run, the reindexing of all previously archived content which occurs the first time you start 2.0-alpha6 after upgrading from 2.0-alpha5 may take prohibitively long. This performance issue will be addressed in the next release. If you do not need the previously stored content during alpha testing, you could delete it and skip this reindexing step; see :doc:`/sysadmin/resetting`.
