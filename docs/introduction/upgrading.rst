================================
Upgrading From LOCKSS 2.0-alpha2
================================

--------------------
Recommended Approach
--------------------

If you have been using LOCKSS 2.0-alpha2 (or LOCKSS 2.0-alpha1, or the LOCKSS 2.0-alpha technology preview), we thank you for helping us bring LOCKSS 2.0 closer to fruition through your testing and feedback.

Although there is an upgrade path from LOCKSS 2.0-alpha2, LOCKSS 2.0-alpha3 is organized significantly differently than prior alpha releases, and we recommend :doc:`installing LOCKSS 2.0-alpha3 from scratch <../installing/index>` when possible.

------------
Upgrade Path
------------

If you intend to upgrade a LOCKSS 2.0-alpha2 system, please read this section.

Updating the LOCKSS Installer
=============================

On the command line, in the ``lockss-installer`` directory, type:

.. code-block::

   git checkout master
   git pull

to update to the latest version of ``lockss-installer`` from GitHub.

Running the Upgrade Command
===========================

On the command line in the updated ``lockss-installer`` directory, type:

.. code-block::

   sudo scripts/upgrade-alpha2-to-alpha3

The script will purge your Docker environment of components, configuration files and images used by the LOCKSS system.

Installing Snap and MicroK8s
============================

The LOCKSS system's containers are no longer orchestrated by Docker Swarm and no longer require Docker to run. The system now uses **MicroK8s**, a lightweight Kubernetes environment. To install the MicroK8s application package, you will need to install and use **Snap**. See :doc:`../installing/snap` and :doc:`../installing/microk8s`.

Modifying the Environment
=========================

In order for LOCKSS 2.0-alpha3 to work properly, you will need to disable frontends to ``iptables`` like ``firewalld`` or ``ufw``, and configure MicroK8s to use DNS in a way that avoids loopback addresses. See :doc:`../installing/firewall` and :doc:`../installing/dns` for details.

Reconfiguring the System
========================

Upon successful completion, you will prompted to run :doc:`scripts/configure-lockss <../configuring>`. **Be advised that the configuration process will prompt you for the PostgreSQL database password.**

Starting LOCKSS
===============

Once configuration is complete you can run lockss as usual with :doc:`scripts/start-lockss <../running>`.
