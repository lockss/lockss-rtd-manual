=========================
Running the LOCKSS System
=========================

The commands in this section are all run as the ``lockss`` user [#fnlockss]_ in the :ref:`LOCKSS Installer Directory`.

--------------------------
Starting the LOCKSS System
--------------------------

To start the LOCKSS system, run the following command:

.. code-block:: shell

   scripts/start-lockss

The :program:`start-lockss` accepts some options:

``--wait`` (``-w``)
   Wait for an internal signal from the system that the its components are initialized. (Currently this internal signal comes from the poller service.)

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

   See :doc:`/sysadmin/lockss`
