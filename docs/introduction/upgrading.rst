================================
Upgrading From LOCKSS 2.0-alpha3
================================

If you are installing LOCKSS 2.x for the first time, proceed to :doc:`/installing/index`.

If you have been running LOCKSS 2.0-alpha3 (or an earlier 2.x version), we thank you for helping us bring LOCKSS 2.0 closer to fruition through your testing and feedback.

-----------------------------
Updating the LOCKSS Installer
-----------------------------

In the ``lockss`` user's ``lockss-installer`` directory, run these commands:

.. code-block::

   git switch master

   git pull

to update to the latest version of ``lockss-installer`` from GitHub.

.. admonition:: Troubleshooting

   If ``git switch master`` fails with the error message ``git: 'switch' is not a git command. See 'git --help'.`` try ``git checkout master`` instead.

------------------------------
Uninstalling MicroK8s and Snap
------------------------------

After 2.0-alpha3, Microk8s, and therefore Snap (except on Ubuntu), are no longer needed. Run the following command:

.. code-block:: shell

   scripts/upgrades/uninstall-microk8s

Portions of this script require the ``lockss`` user's :program:`sudo` password. The :program:`uninstall-microk8s` script will ask you to confirm before uninstalling Snap (:program:`snapd`).

.. caution::

   **On Ubuntu, Snap is used natively by the operating system and should not be uninstalled.**

------------------------
Restoring Packet Filters
------------------------

One of the short-term requirement of 2.0-alpha3 was that frontends to :program:`iptables` like :program:`firewalld` or :program:`ufw` be disabled, to work more smoothly with MicroK8s. This is no longer necessary in most cases.

Select your operating system below to see information about re-enabling packet filters:

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

Another short-term requirement of 2.0-alpha3 was that the ``lockss`` user have a login password set and be allowed access to :program:`sudo`. This is also no longer needed. It is recommended you revoke these extra privileges for better security.

To invalidate the login password of the ``lockss`` user, run this command as ``root`` or with :program:`sudo`:

.. code-block:: shell

   usermod --lock lockss

Select your operating system below to see information about revoking the ``lockss`` user's access to :program:`sudo`:

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
Reconfiguring the System
------------------------

Finally, you need to reconfigure your LOCKSS system by running the :program:`configure-lockss` script again. Proceed to :doc:`/configuring` for details.
