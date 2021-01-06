================================
Upgrading From LOCKSS 2.0-alpha1
================================

If you have been using version 2.0-alpha1 of the LOCKSS system, an upgrade path has been provided to version 2.0-alpha2.

-------------
Prerequisites
-------------

See :doc:`installing/index`. Additionally you will need to :doc:`install OpenJDK8 <installing/openjdk8>` on the host machine.

.. note::

   This dependency on Java is temporary for 2.0-alpha2. It is necessary to run the Solr upgrader tool. In 2.0-alpha3, the process will be packaged in such a way that it does not depend on Java on the host machine.

---------------------------
Update ``lockss-installer``
---------------------------

On the command line in the :file:`lockss-installer` directory, type:

.. code-block:: shell

   git checkout master

   git pull

to update to the latest version of :file:`lockss-installer` from GitHub.

-----------------------
Run the Upgrade Command
-----------------------

On the command line in the :file:`lockss-installer` directory, type:

.. code-block:: shell

   sudo scripts/upgrade-alpha1-to-alpha2

The script will perform a number of system-level changes and need to be ``root``.

These adjustments include renaming :file:`config.info` to :file:`system.cfg`, shutting down a running system stack, renaming storage directories, updating database names, run the Solr upgrader tool from 2.0-alpha1 to 2.0-alpha2 (which is a long running process; please be patient), and change file ownerships, all of which to align the system with the 2.0-alpha2 environment.

-----------------------
Re-Configure the System
-----------------------

Upon successful completion, you will prompted to run :file:`scripts/configure-lockss`. **Be advised that the configuration process will prompt you for the Postgres database password.**
