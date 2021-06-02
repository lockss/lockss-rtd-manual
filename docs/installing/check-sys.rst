===================
Checking the System
===================

**FIXME this needs to be updated for alpha4**

After `installing the LOCKSS system <index>`_, you can confirm the status of installed components by running:

.. code-block:: shell

   sudo scripts/check-sys

in the :file:`lockss-installer` directory.

The script will do its best to check for any missing elements and permissions needed to run the LOCKSS cluster on the host machine:

*  Check for Snap
*  Check for MicroK8s
*  Check for a user ``lockss``.
*  Check user ``lockss`` has appropriate group memberships and permissions.
