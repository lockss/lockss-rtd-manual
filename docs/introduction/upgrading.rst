================================
Upgrading From LOCKSS 2.0-alpha3
================================

If you are installing LOCKSS 2.x for the first time, proceed to :doc:`/installing/index`.

If you have been running LOCKSS 2.0-alpha3 (or an earlier 2.x version), we thank you for helping us bring LOCKSS 2.0 closer to fruition through your testing and feedback.

-------------------------
Purging LOCKSS 2.0-alpha3
-------------------------

The first step is to stop the LOCKSS 2.0-alpha3 system and purge it from the current Kubernetes environment (run by MicroK8s).

Log in as the ``lockss`` user and run this command in the :file:`lockss-installer` directory:

.. code-block:: shell

   scripts/uninstall-lockss

-----------------------------
Updating the LOCKSS Installer
-----------------------------

The next step is to update the LOCKSS installer to its latest version from GitHub.

While still logged in as ``lockss`` and in the :file:`lockss-installer` directory, run these commands:

.. code-block::

   git checkout master

   git pull

------------------------------
Uninstalling MicroK8s and Snap
------------------------------

After 2.0-alpha3, Microk8s, and therefore Snap (except on Ubuntu), are no longer needed.

While still logged in as ``lockss`` and in the :file:`lockss-installer` directory, run this command:

.. code-block:: shell

   scripts/upgrades/uninstall-microk8s

Portions of this script require the ``lockss`` user's :program:`sudo` password. The :program:`uninstall-microk8s` script will ask you to confirm before uninstalling Snap (:program:`snapd`).

.. caution::

   **On Ubuntu, Snap is used natively by the operating system and should not be uninstalled.**

----------------------------------------------------
Revoking the Extra Privileges of the ``lockss`` User
----------------------------------------------------

A short-term requirement of 2.0-alpha3 was that the ``lockss`` user have a login password set and be allowed access to :program:`sudo`. This is no longer needed. We strongly recommend you revoke these extra privileges for better security.

Follow the following steps:

1. Log out of the ``lockss`` user account. You can do this by typing ``exit`` or ``logout``, or hitting :kbd:`Ctrl + D` on the keyboard.

2. Log in as a user other than ``lockss`` with :program:`sudo` privileges [#fn1]_ .

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

------------------------
Restoring Packet Filters
------------------------

Another short-term requirement of 2.0-alpha3 was that frontends to :program:`iptables` like :program:`firewalld` or :program:`ufw` be disabled, to work more smoothly with MicroK8s. This is also no longer necessary in most cases.

To re-enable packet filters, select your operating system below and follow the corresponding instructions while still logged in as a user other than ``lockss`` with :program:`sudo` privileges [#fn1]_ :

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

--------------
Installing K3s
--------------

Next, you will need to install K3s, a lightweight Kubernetes environment to replace MicroK8s.

Proceed to the :doc:`/installing/k3s` section of the :doc:`/installing/index` chapter, skipping over the earlier sections of the chapter that are not required in an upgrade situation (:doc:`/installing/user`, :doc:`/installing/git`, :doc:`/installing/lockss-installer`).

Then simply continue following the manual from the :doc:`/installing/k3s` section forward. In particular, you will need to re-run the configuration script (see :doc:`/configuring`).

----

.. rubric:: Footnotes

.. [#fn1] Alternatively, you can log in as ``root``, in which case issue all commands without the leading :program:`sudo`.
