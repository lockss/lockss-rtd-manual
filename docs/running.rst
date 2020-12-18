=========================
Running the LOCKSS System
=========================

--------------------------
Starting the LOCKSS System
--------------------------

Run ``scripts/start-lockss``. This script will call in turn:

   *  ``scripts/generate-lockss``: This script takes your configuration data and turns it into a set of configuration files containing the right values.

   *  ``scripts/assemble-lockss``: This script puts the configuration files and puts them in the right places, and ensures that all storage volumes are ready for use (creating them if necessary).

   *  ``scripts/deploy-lockss``: This script deploys your LOCKSS stack by invoking Kubernetes.

-------------------------------
Shutting down the LOCKSS System
-------------------------------

Run ``scripts/shutdown-lockss``.

----------------------------------
Restarting a Running LOCKSS System
----------------------------------

Run ``scripts/restart-lockss``.

-----------------------------------
Removing a Configured LOCKSS System
-----------------------------------

To remove all configurations, volumes and networks installed by the LOCKSS system, run ``scripts/uninstall-lockss``. This will **not** remove files from the persistent store.
