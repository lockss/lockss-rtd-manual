================================
Upgrading From LOCKSS 2.0-alpha4
================================

.. note::

   **This chapter describes how to upgrade an existing LOCKSS 2.0-alpha4 system to 2.0-beta1.**

   *  **If you are migrating an existing LOCKSS 1.x system to LOCKSS 2.0-beta1**, go to :doc:`/appendix/migrating` instead.

   *  **If you are installing the LOCKSS system for the first time**, go to :doc:`/installing/index` instead.

.. tip::

   Before you begin upgrading from 2.0-alpha4, we strongly recommend you first bring your operating system up to date by applying security updates and upgrading installed packages. Ask your system administrator or see :doc:`/appendix/os-updates` in the appendix.

*  **FIXME** Please note that the upgrade process includes re-running the LOCKSS configuration tool, which **will require you to re-enter the PostgreSQL database password**.

.. contents:: Chapter Overview
   :local:
   :depth: 1

| **FIXME**
| **FIXME**
| **FIXME**

--------------------------
Stopping LOCKSS 2.0-alpha4
--------------------------

The first step is to stop the LOCKSS 2.0-alpha4 system.

Log in as the ``lockss`` user and run this command in the :file:`lockss-installer` directory:

.. code-block:: shell

   scripts/stop-lockss

-----------------------------
Updating the LOCKSS Installer
-----------------------------

The next step is to update the LOCKSS installer to its latest version from GitHub.

While still logged in as ``lockss`` and in the :file:`lockss-installer` directory, run these commands:

.. code-block:: shell

   git checkout master

   git pull

--------------------------
Adjusting File Permissions
--------------------------

Some files stored on disk in 2.0-alpha3 and prior are owned by ``root``.

While still logged in as ``lockss`` and in the :file:`lockss-installer` directory, run this command:

.. code-block:: shell

   scripts/upgrades/fix-permissions

You may be prompted for the ``lockss`` user's :program:`sudo` password.

------------------------------
Uninstalling MicroK8s and Snap
------------------------------

After 2.0-alpha3, Microk8s, and therefore Snap (except on Ubuntu), are no longer needed.

While still logged in as ``lockss`` and in the :file:`lockss-installer` directory, run this command:

.. code-block:: shell

   scripts/upgrades/uninstall-microk8s

You may be prompted for the ``lockss`` user's :program:`sudo` password.

The :program:`uninstall-microk8s` script will ask you to confirm before uninstalling Snap (:program:`snapd`). Enter :kbd:`Y` for "yes" and :kbd:`N` for "no", or simply hit :kbd:`Enter` to accept the suggested answer in square brackets.

.. caution::

   **On Ubuntu, Snap is used natively by the operating system and should not be uninstalled.**

------------------------
Restoring Packet Filters
------------------------

A short-term requirement of 2.0-alpha3 was that frontends to :program:`iptables` like :program:`firewalld` or :program:`ufw` be disabled, to work more smoothly with MicroK8s. This is no longer necessary in most cases, and you should return your system's :program:`firewalld` or :program:`ufw` to its original state.

If you had disabled :program:`firewalld` or :program:`ufw` to run 2.0-alpha3, select your operating system below and follow the corresponding instructions while still logged in as ``lockss``:

.. tabs::

   .. group-tab:: CentOS

      .. include:: upgrading-firewalld.rst

   .. group-tab:: Debian

      .. include:: upgrading-none.rst

   .. group-tab:: Linux Mint

      .. include:: upgrading-none.rst

   .. group-tab:: OpenSUSE

      .. include:: upgrading-firewalld.rst

   .. group-tab:: RHEL

      .. include:: upgrading-firewalld.rst

   .. group-tab:: Ubuntu

      .. include:: upgrading-ufw.rst

----------------------------------------------------
Revoking the Extra Privileges of the ``lockss`` User
----------------------------------------------------

Another short-term requirement of 2.0-alpha3 was that the ``lockss`` user have a login password set and be allowed access to :program:`sudo`. This is no longer needed and we strongly recommend you revoke these extra privileges for better security.

Follow the following steps:

1. Log out of the ``lockss`` user account. You can do this by typing ``exit`` or ``logout``, or hitting :kbd:`Ctrl + D` on the keyboard.

2. Log in as a privileged user other than ``lockss`` privileged user who can become root via :program:`sudo` [#fnprivileged]_.

3. To invalidate the login password of the ``lockss`` user, run this command:

   .. code-block:: shell

      sudo usermod --lock lockss

4. To revoke the ``lockss`` user's access to :program:`sudo`, select your operating system below and follow the corresponding instructions.

   .. tabs::

      .. group-tab:: CentOS

         .. include:: upgrading-wheel.rst

      .. group-tab:: Debian

         .. include:: upgrading-sudo.rst

      .. group-tab:: Linux Mint

         .. include:: upgrading-sudo.rst

      .. group-tab:: OpenSUSE

         .. include:: upgrading-wheel.rst

      .. group-tab:: RHEL

         .. include:: upgrading-wheel.rst

      .. group-tab:: Ubuntu

         .. include:: upgrading-sudo.rst

----------
Next Steps
----------

Next, you will need to install K3s, a lightweight Kubernetes environment to replace MicroK8s.

Proceed to the :doc:`/installing/k3s` section of the :doc:`/installing/index` chapter, skipping over the earlier sections of the chapter that are not required in an upgrade situation (:doc:`/installing/user`, :doc:`/installing/downloading`).

Then simply continue following the manual from the :doc:`/installing/k3s` section forward. In particular, you will need to re-run the configuration script (see :doc:`/configuring`).

----

.. rubric:: Footnotes

.. [#fnprivileged]

   See :doc:`/appendix/privileged`.
