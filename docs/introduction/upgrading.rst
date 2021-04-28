================================
Upgrading From LOCKSS 2.0-alpha3
================================

If you are installing LOCKSS 2.x for the first time, proceed to :doc:`/installing/index`.

If you have been running LOCKSS 2.0-alpha3 (or an earlier 2.x version), we thank you for helping us bring LOCKSS 2.0 closer to fruition through your testing and feedback.

Although there is an upgrade path from LOCKSS 2.0-alpha3, LOCKSS 2.0-alpha4 is organized differently than prior alpha releases, and we recommend installing LOCKSS 2.0-alpha4 from scratch when possible.

------------------------------
Stopping the 2.0-alpha3 System
------------------------------

If your LOCKSS 2.0-alpha3 system is currently running, first shut it down with this command:

.. code-block:: shell

   scripts/shutdown-lockss

*FIXME scripts/uninstall-lockss*

-----------------------------
Updating the LOCKSS Installer
-----------------------------

On the command line, in the ``lockss-installer`` directory, type:

.. code-block::

   git checkout master

   git pull

to update to the latest version of ``lockss-installer`` from GitHub.

---------------------
Uninstalling MicroK8s
---------------------

To uninstall MicroK8s, use this Snap command:

.. code-block:: shell

   sudo snap remove microk8s

-----------------
Uninstalling Snap
-----------------

To uninstall Snap, follow the suggested procedure for your operating system:

.. tabs::

   .. group-tab:: CentOS

      .. tabs::

         .. group-tab:: CentOS 7

            .. include:: upgrading-yum.rst

         .. group-tab:: CentOS 8

            .. include:: upgrading-dnf.rst

   .. group-tab:: Debian

      .. include:: upgrading-apt.rst

   .. group-tab:: Linux Mint

      .. include:: upgrading-apt.rst

   .. group-tab:: OpenSUSE

      .. include:: upgrading-zypper.rst

   .. group-tab:: RHEL

      .. tabs::

         .. group-tab:: RHEL 7

            .. include:: upgrading-yum.rst

         .. group-tab:: RHEL 8

            .. include:: upgrading-dnf.rst

   .. group-tab:: Ubuntu

      In recent versions of Ubuntu, Snap is the native way many applications are installed and run, so **uninstalling Snap is not advised**.

-------------------------
Modifying the Environment
-------------------------

FIXME

In order for LOCKSS 2.0-alpha3 to work properly, you will need to disable frontends to ``iptables`` like ``firewalld`` or ``ufw``, and configure MicroK8s to use DNS in a way that avoids loopback addresses. See :doc:`../installing/firewall` and :doc:`../installing/dns` for details.

------------------------
Reconfiguring the System
------------------------

FIXME

Upon successful completion, you will prompted to run :doc:`scripts/configure-lockss <../configuring>`. **Be advised that the configuration process will prompt you for the PostgreSQL database password.**
