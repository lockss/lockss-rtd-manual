============================
Creating the ``lockss`` User
============================

The LOCKSS system runs under a system user named ``lockss``, which is in a group named ``lockss``, and which is capable of using :program:`sudo`. *FIXME: how narrowly/broadly needed is sudo?*

.. important::

   See the :doc:`../introduction/security` section for more about this short-term requirement. *FIXME: is the warning still needed?*

----------------------------
Creating the ``lockss`` User
----------------------------

Follow the instructions for your Linux flavor:

.. tabs::

   .. group-tab:: Arch Linux

      .. include:: user-wheel.rst

   .. group-tab:: CentOS

      .. include:: user-wheel.rst

   .. group-tab:: Debian

      .. include:: user-sudo.rst

   .. group-tab:: Fedora

      .. include:: user-wheel.rst

   .. group-tab:: Linux Mint

      .. include:: user-sudo.rst

   .. group-tab:: OpenSUSE

      .. include:: user-wheel.rst

   .. group-tab:: RHEL

      .. include:: user-wheel.rst

   .. group-tab:: Ubuntu

      .. include:: user-sudo.rst

-------------------------------
Setting the ``lockss`` Password
-------------------------------

Run the following command (as ``root`` or with :program:`sudo`):

.. code-block:: shell

   passwd lockss

You will be prompted for a password for the ``lockss`` user (twice). On some systems, :program:`passwd` displays warnings or fails if the supplied password does not meet certain complexity criteria.

--------------------------------
Switching to the ``lockss`` User
--------------------------------

All commands shown in this document except those that explicitly invoke ``sudo`` should be issued from a shell running as the ``lockss`` user. Depending on your preference, you may login as ``lockss``, or switch to the ``lockss`` user with this command:

.. code-block::

   sudo -i -u lockss
