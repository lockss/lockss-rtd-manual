================================
Upgrading From LOCKSS 2.0-alpha5
================================

.. note::

   .. COMMENT PREVIOUSVERSION

   .. COMMENT LATESTVERSION

   This chapter describes how to upgrade an existing LOCKSS 2.0-alpha5 system to 2.0-alpha6. Are you installing the LOCKSS 2.x system for the first time? Go to:

   .. button-ref:: /installing/index
      :ref-type: doc
      :color: primary
      :align: center

.. tip::

   Before you begin the upgrade, we strongly recommend you first bring your operating system up to date by applying security updates and upgrading installed packages. Ask your system administrator or see :doc:`/sysadmin/os-updates` in the appendix.

**FIXME FIXME FIXME**


.. COMMENT PREVIOUSVERSION

----------------------
Stop LOCKSS 2.0-alpha5
----------------------

.. COMMENT PREVIOUSVERSION

The first step is to stop the LOCKSS 2.0-alpha5 system.

Log in as the ``lockss`` user and run the following command in the :file:`lockss-installer` directory:

.. code-block:: shell

   scripts/stop-lockss

---------------------------
Update the LOCKSS Installer
---------------------------

The official way to download the LOCKSS Installer is now through the LOCKSS Downloader, rather than cloning the LOCKSS Installer as a Git project as in previous releases. However, advanced users may continue to use :program:`git` if they wish (see :doc:`/appendix/git-downloader` for instructions).

.. COMMENT PREVIOUSVERSION

Move the existing 2.0-alpha5 LOCKSS Installer out of the way:

.. COMMENT PREVIOUSVERSION

.. code-block:: shell

   mv lockss-installer lockss-installer.alpha5

.. COMMENT PREVIOUSVERSION

Then follow the steps in :doc:`/installing/index` to download the 2.0-alpha6 version of the LOCKSS Installer, skipping over the earlier sections of the chapter that are not required in the context of an upgrade (e.g., :doc:`/installing/user`).

----------------------
Run the Upgrade Script
----------------------

**FIXME**

We have provided an upgrade script to upgrade on-disk structures. To run it, log in as the ``lockss`` user and run the following command in the :file:`lockss-installer` directory:

.. code-block:: shell

   scripts/upgrades/upgrade-alpha4-to-alpha5

---------------------------
Re-run the Configure Script
---------------------------

.. COMMENT LATESTVERSION

Copy the existing LOCKSS system configuration into the new 2.0-alpha6 environment:

.. COMMENT PREVIOUSVERSION

.. code-block:: shell

   cp lockss-installer.alpha5/config/system.cfg lockss-installer/config/system.cfg

.. COMMENT FIXME :doc: syntax error

Then follow the instructions in :doc:`configuring` to ensure all existing configuration parameters are still correct and to configure any new parameters.

----------
Next Steps
----------

.. COMMENT LATESTVERSION

.. COMMENT FIXME :doc: syntax error

Follow the instructions in :doc:`running` to start your LOCKSS 2.0-alpha6 instance.

.. note::

   **FIXME**

   .. COMMENT PREVIOUSVERSION

   .. COMMENT LATESTVERSION

   The first time 2.0-alpha6 is started after an upgrade from 2.0-alpha5, it may take several minutes before the system becomes available, while it re-indexes all previously archived content.
