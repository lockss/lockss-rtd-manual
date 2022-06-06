================================
Upgrading From LOCKSS 2.0-alpha5
================================

**FIXME FIXME FIXME**

.. COMMENT LATESTVERSION

.. note::

   This chapter describes how to upgrade an existing LOCKSS 2.0-alpha5 system to 2.0-beta1.

   If you are installing the LOCKSS system for the first time, go to :doc:`/installing/index` instead.

.. tip::

   Before you begin the upgrade, we strongly recommend you first bring your operating system up to date by applying security updates and upgrading installed packages. Ask your system administrator or see :doc:`/sysadmin/os-updates` in the appendix.

----------------------
Stop LOCKSS 2.0-alpha4
----------------------

The first step is to stop the LOCKSS 2.0-alpha4 system.

Log in as the ``lockss`` user and run the following command in the :file:`lockss-installer` directory:

.. code-block:: shell

   scripts/stop-lockss

---------------------------
Update the LOCKSS Installer
---------------------------

The official way to download the LOCKSS Installer is now through the LOCKSS Downloader, rather than cloning the LOCKSS Installer as a Git project as in previous releases. However, advanced users may continue to use :program:`git` if they wish (see :doc:`/appendix/git-downloader` for instructions).

Move the existing 2.0-alpha4 LOCKSS Installer out-of-the-way:

.. code-block:: shell

   mv lockss-installer lockss-installer.alpha4

Then follow the steps in :doc:`/installing/index` to download the 2.0-alpha5 version of the LOCKSS Installer, skipping over the earlier sections of the chapter that are not required in the context of an upgrade (e.g., :doc:`/installing/user`).

----------------------
Run the Upgrade Script
----------------------

We have provided an upgrade script to upgrade on-disk structures. To run it, log in as the ``lockss`` user and run the following command in the :file:`lockss-installer` directory:

.. code-block:: shell

   scripts/upgrades/upgrade-alpha4-to-alpha5

---------------------------
Re-run the Configure Script
---------------------------

Copy the existing LOCKSS system configuration into the new 2.0-alpha5 environment:

.. code-block:: shell

   cp lockss-installer.alpha4/config/system.cfg lockss-installer/config/system.cfg

Then follow the instructions in :doc:`configuring` to ensure all existing configuration parameters are still correct and to configure any new parameters.

----------
Next Steps
----------

Follow the instructions in :doc:`running` to start your LOCKSS 2.0-alpha5 instance.

.. note::

   The first time 2.0-alpha5 is started after an upgrade from 2.0-alpha4, it may take several minutes before the system becomes available, while it re-indexes all previously archived content.
