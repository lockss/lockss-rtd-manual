================================
Upgrading From LOCKSS 2.0-alpha5
================================

.. note::

   .. COMMENT PREVIOUSVERSION

   .. COMMENT LATESTVERSION

   This chapter describes how to upgrade an existing LOCKSS 2.0-alpha5 system to 2.0-alpha6. If you are installing the
   LOCKSS 2.x system for the first time, please see the Installation instructions:

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

The first step is to stop the LOCKSS 2.0-alpha5 system. Log in as the ``lockss`` user and run the following 
command in your :file:`lockss-installer` directory. The default location of this directory is within the 
``lockss`` user's home directory :file:`{$HOME}/lockss-installer` (which typically resolves to 
:file:`/home/lockss/lockss-installer`).

.. code-block:: shell

   scripts/stop-lockss

You may verify all LOCKSS components have stopped by running the following command:

.. code-block:: shell

   k3s kubectl get deployments -n lockss

Which should return:

.. code-block:: text

   No resources found in lockss namespace.

---------------------------
Update the LOCKSS Installer
---------------------------

As of alpha5, the official way to install and upgrade the LOCKSS Installer is using the LOCKSS Downloader, rather than
cloning the LOCKSS Installer as a Git project. The instructions below detail the use of the LOCKSS Downloader. Advanced
users may continue to use :program:`git` if they wish (please see :doc:`/appendix/git-downloader` for instructions).

As the ``lockss`` user, run either this :program:`curl` command:

.. code-block:: shell

   curl -sSfL https://www.lockss.org/downloader | sh -s -

Or this :program:`wget` command:

.. code-block:: shell

   wget -qO- https://www.lockss.org/downloader | sh -s -

This will download and invoke the LOCKSS Downloader, which in turn will install the latest version of the LOCKSS
Installer into the existing LOCKSS Installer installation (by default, :file:`{$HOME}/lockss-installer`, which typically
resolves to :file:`/home/lockss/lockss-installer`).

.. tip::

   The LOCKSS Downloader has command line arguments that can customize your LOCKSS Installer installation:

   * To upgrade a LOCKSS Installer in another directory :samp:`{DIR}`, add :samp:`--download-dir={DIR}` after
     ``sh -s -``, like so:

   .. code-block:: shell

      ... | sh -s - --download-dir=DIR

   .. COMMENT PREVIOUS VERSION

   * To install a specific version of the LOCKSS Installer, the LOCKSS Downloader the :samp:`--git-branch`,
     :samp:`--git-commit`, :samp:`--git-tag` options. Developers testing the latest pre-release version of the LOCKSS
     Installer should use the `develop` branch, like so:

   .. code-block:: shell

      ... | sh -s - --git-branch=develop

----------------------
Run the Upgrade Script
----------------------

The next step is to update archived content from the previous release version. Log in as the ``lockss`` user and run the 
following command from the :file:`lockss-installer` directory:

.. code-block:: shell

   scripts/upgrades/upgrade-to-alpha6

.. note::

   It may take several minutes for the upgrade script to make a backup of your existing Solr index.

---------------------------
Re-run the Configure Script
---------------------------

.. COMMENT FIXME :doc: syntax error

Re-run the configuration script by running the command below and follow the instructions in :doc:`configuring` to ensure all existing 
configuration parameters are still correct and to configure any new parameters.

.. code-block:: shell

   scripts/configure-lockss

----------
Next Steps
----------

.. COMMENT LATESTVERSION

.. COMMENT FIXME :doc: syntax error

Follow the instructions in :doc:`running` to start your LOCKSS 2.0-alpha6 instance.

.. code-block:: shell

   scripts/start-lockss

.. note::

   .. COMMENT PREVIOUSVERSION

   .. COMMENT LATESTVERSION

   The first time 2.0-alpha6 is started after an upgrade from 2.0-alpha5, it may take several minutes before the system becomes available, while it re-indexes all previously archived content.
