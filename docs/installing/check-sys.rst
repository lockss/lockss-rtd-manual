===================
Checking the System
===================

After :doc:`installing the LOCKSS system <index>` and :doc:`downloading the LOCKSS Installer <lockss-installer>`, prepare the system for running by typing:

.. code-block:: shell

   scripts/check_sys

in the :file:`lockss-installer` directory.

The script will do its best to install any missing elements needed to run the LOCKSS cluster on the host machine. See the :doc:`prerequisites` document for required system elements.

1. Check for Docker and install if missing.
2. Check for the Local-Persist Docker volume plugin and install if missing.
3. Ensure Docker Swarm is initialized and running.
4. Check for a user ``lockss`` and create the ``lockss`` user and group if missing.
