================
Upgrading LOCKSS
================

This chapter describes how to **upgrade an existing LOCKSS 2.0 installation** to |LOCKSS| |LATEST_MINOR| from any release of LOCKSS 2.0-alpha5, LOCKSS 2.0-alpha6, LOCKSS 2.0-alpha7, or LOCKSS 2.0-beta1. Please note:

*  If you are **installing** LOCKSS |LATEST_MINOR| **from scratch**, follow the instructions in :doc:`/installing/index` instead.

*  If you are **upgrading an existing LOCKSS 1.x installation** to LOCKSS |LATEST_MINOR|, follow the instructions in :doc:`lockss-portal:migration/index` instead.

.. attention::

   Almost all network ports used in the :term:`LOCKSS stack` changed in |LOCKSS| 2.0-beta2 compared to earlier "alpha" and "beta" versions of LOCKSS 2.0, which impacts :term:`firewall` rules, browser bookmarks, scripts, and more. For example, the port for the Web user interface of the :ref:`LOCKSS Configuration Service`, often used when first logging in to LOCKSS in a browser, has moved from 24621 to 24602. See :ref:`LOCKSS 2.0-beta2 Port Changes`.

To upgrade to LOCKSS |LATEST_PATCH|, follow these steps:

1. Before you begin the upgrade process, we recommend you first bring your operating system up to date by applying security updates and upgrading installed packages. Ask your system administrator or see :doc:`/sysadmin/os-updates` in the appendix.

2. Establish a console session as the ``lockss`` user.

3. Navigate to the :ref:`LOCKSS Installer Directory`, symbolically:

   :samp:`cd {<LOCKSS_INSTALLER_DIR>}`

4. Stop the :term:`LOCKSS stack` with this command:

   .. code-block:: shell

      scripts/stop-lockss

5. .. index:: Curl, Wget, runuser

   Download the latest version of the :term:`LOCKSS Installer` with the following :term:`Curl` or :term:`Wget` command [#fnfetcher]_:

   .. tab-set::

      .. tab-item:: Curl
         :sync: curl

         .. code-block:: shell

            curl -sSfL https://lockss.org/downloader | sh -s - --download-dir=`pwd`

      .. tab-item:: Wget
         :sync: wget

         .. code-block:: shell

            wget -qO- https://lockss.org/downloader | sh -s - --download-dir=`pwd`

6. .. index:: K3s; upgrade

   The next task is to upgrade :term:`K3s` from 1.21 to 1.31.

   .. important::

      This task is performed as ``root``, in the :ref:`LOCKSS Installer Directory` (:samp:`cd {<LOCKSS_INSTALLER_DIR>}`).

   a. First, run (as ``root``):

      .. code-block:: shell

         scripts/install-lockss --install-k3s

      .. tip::

         This runs the :term:`K3s Installer` -- the installation script provided by :term:`K3s` itself. The warning or error messages that may occur while it runs vary. If this step fails, see the suggestions in the equivalent section of the manual for a first-time installation: :numref:`Installing K3s` (:ref:`Installing K3s`).

   b. Then, run (as ``root``):

      .. code-block:: shell

         scripts/install-lockss --test-k3s

      .. tip::

         If this step fails, see the suggestions in the equivalent section of the manual for a first-time installation: :numref:`Testing the K3s Node` (:ref:`Testing the K3s Node`).

7. Return to your ongoing ``lockss`` console session. Double-check that you are operating as ``lockss`` by typing:

   .. code-block:: shell

      whoami

   and verifying that the output is ``lockss``.

8. Next, you will upgrade LOCKSS from a version 2.0-alpha5 or greater to LOCKSS |LATEST_PATCH|. Run this command:

   .. code-block:: shell

      scripts/upgrades/upgrade-to-beta2

9. If :program:`upgrade-to-beta2` succeeds, it will direct you to run :term:`configure-lockss`; run this command:

   .. code-block:: shell

      scripts/configure-lockss --replay

   .. tip::

      If any configuration question requires input, see a reference of all of :program:`configure-lockss` in :numref:`Configuring LOCKSS` (:ref:`Configuring LOCKSS`).

10. Finally, start the LOCKSS stack with this command:

   .. code-block:: shell

      scripts/start-lockss

   .. note::

      LOCKSS 2.0-beta2 now uses PostgreSQL for its artifact index, which needs to be populated upon the first startup by examining all artifacts in storage. This initial inventory may take a long time, proportional to the amount of preserved content.

----

.. [#fnfetcher]

   Most typical Linux systems have at least one of `Curl <https://curl.se/>`_ or `Wget <https://www.gnu.org/software/wget/>`_ installed by default. You can check by typing ``curl --version`` or ``wget --version`` and seeing which ones do not output an error message. See :doc:`/sysadmin/curl` or :doc:`/sysadmin/wget` for installation instructions.
