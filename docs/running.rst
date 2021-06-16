=========================
Running the LOCKSS System
=========================

The commands in this section are all run as the ``lockss`` user [#fnlockss]_ in the ``lockss`` user's :file:`lockss-installer` directory.

--------------------------
Starting the LOCKSS System
--------------------------

Run ``scripts/start-lockss``. This script will call in turn:

   *  ``scripts/generate-lockss``: This script takes your configuration data and turns it into a set of configuration files containing the right values.

   *  ``scripts/assemble-lockss``: This script puts the configuration files and puts them in the right places, and ensures that all storage volumes are ready for use (creating them if necessary).

   *  ``scripts/deploy-lockss``: This script deploys your LOCKSS stack by invoking Kubernetes.

The :program:`start-lockss` accepts some options:

``--update`` (``-u``)
   Force the system to check for newer container images of the system's components (LOCKSS services, embedded databases, embedded Web replay engines...) before deploying the system to Kubernetes.

``--wait`` (``-w``)
   After deploying the system to Kubernetes and waiting for the system's containers to come up, additionally wait for an internal signal from the system that the system's components are fully initialized. (Currently this internal signal comes from the poller service.)

-------------------------------
Shutting down the LOCKSS System
-------------------------------

Run ``scripts/stop-lockss``.

----------------------------------
Restarting a Running LOCKSS System
----------------------------------

Run ``scripts/restart-lockss``.

The :program:`restart-lockss` accepts the same options as :program:`start-lockss`.

-----------------------------------
Removing a Configured LOCKSS System
-----------------------------------

To remove all configurations, volumes and networks configured by the LOCKSS system in Kubernetes, run ``scripts/uninstall-lockss``. This will **not** remove files from the persistent store.

----

.. rubric:: Footnotes

.. [#fnlockss]

   See :doc:`/appendix/lockss`
