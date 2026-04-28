==================
Configuring LOCKSS
==================

.. note::

   Commands in this section are run as the ``lockss`` user.

.. only:: html and not singlehtml

   .. sidebar::

      .. contents:: Section Table of Contents
         :local:
         :depth: 1
         :backlinks: none

.. index:: ! configure-lockss

After :doc:`installing the LOCKSS stack </installing/index>`, you will configure it with the :term:`LOCKSS Installer`'s :program:`configure-lockss` script [#fn-hostconfig]_.

.. index:: configure-lockss; preparation

-----------------------------------
Gathering Configuration Information
-----------------------------------

You will need to gather information to answer configuration questions asked by :program:`configure-lockss`, including:

*  The name (FQDN) of the host, the IP address of the host, and if behind NAT, the external IP address for NAT.

*  The mail relay host, and optionally mail credentials, for sending e-mail from the host, and the e-mail address for the administrator of the system.

*  The configuration URL and preservation group or groups corresponding to the LOCKSS network your system is joining.

*  The paths for one or more :term:`content storage areas <content storage area>`, the :term:`state data storage area`, the :term:`temporary storage area`, and the :term:`log storage area`. See the :ref:`Storage Prerequisites` sections for important information about requirements for these storage areas.

   .. caution::

      Each of these paths needs to be writable by the ``lockss`` user. If this is not the case, set them up as ``root`` before running :program:`configure-lockss`.

*  Username and password for the Web user interfaces.

*  A password for the PostgreSQL database.

   *  Alternatively, if using an existing PostgreSQL database, the host name, port, schema, username and password for the external PostgreSQL database, as well as a prefix for database names.

*  Which :ref:`Stack Components` you wish to use.

Some notes about using :program:`configure-lockss`:

*  When run the first time, some of the questions asked by the script will have a suggested or default value, displayed in square brackets; hit :kbd:`Enter` to accept the suggested value, or type the correct value and hit :kbd:`Enter`.

*  Any subsequent runs will use the previous values as the default value; review and hit :kbd:`Enter` to leave unchanged. Use ``configure-lockss --replay`` (or ``configure-lockss -r`` for short) to prompt only for info not already found in the configuration file.

*  Password prompts will not display the previous value but can still be left unchanged with :kbd:`Enter`.

.. index:: configure-lockss; invocation

.. _Invoking configure-lockss:

------------------------------------
Invoking :program:`configure-lockss`
------------------------------------

To invoke :program:`configure-lockss`, follow these steps:

1. Establish a ``lockss`` shell session. Double-check that you are acting as ``lockss`` by typing:

   .. code-block:: shell

      whoami

   and verifying that the output is ``lockss``.

2. Navigate to the :ref:`LOCKSS Installer Directory`, symbolically:

   :samp:`cd {<LOCKSS_INSTALLER_DIR>}`

3. Run this command:

   .. code-block:: shell

      scripts/configure-lockss

The script will begin with the first series of configuration questions from :octicon:`diff-renamed` :numref:`Kubernetes Settings` (:ref:`Kubernetes Settings`).

.. index:: configure-lockss; Kubernetes

-------------------
Kubernetes Settings
-------------------

Prompt: :guilabel:`Command to use to execute kubectl commands`

Enter the command to invoke :program:`kubectl` in your environment. If you are using :term:`K3s`, the :term:`Kubernetes` environment that ships with |LOCKSS|, the proposed value is already correct and you can simply hit :kbd:`Enter` to accept the suggested value in square brackets.

.. FIXME the script can exit here if the K8s (sic) config file can't be written to

.. index:: configure-lockss; network

----------------
Network Settings
----------------

Hostname
========

Prompt: :guilabel:`Fully qualified hostname (FQDN) of this machine`

Enter the machine's fully-qualified hostname (meaning with its domain name), for example :samp:`locksstest.myuniversity.edu`.

IP Address
==========

Prompt: :guilabel:`IP address of this machine`

*  If the host is on the Internet, enter its *publicly routable IP address*.

*  If the host is behind network address translation (NAT), enter its *internal IP address*. You will be asked the other IP address later in :numref:`Network Address Translation` (:ref:`Network Address Translation`).

Initial UI Subnet
=================

Prompt: :guilabel:`Initial subnet(s) for admin UI access, separated by ';'`

Enter a semicolon-separated list of subnets in CIDR or mask notation that should initially have access to the |LOCKSS| Web user interfaces (UIs). The access list can be modified later via the :ref:`LOCKSS Configuration Service` UI.

LCAP Port
=========

Prompt: :guilabel:`LCAP protocol port`

Enter the port on the that will be used to receive :term:`LCAP` traffic. Historically, most LOCKSS nodes use :samp:`9729`.

Network Address Translation
===========================

1. Prompt: :guilabel:`Is this machine behind NAT?`

   If the host is behind network address translation (NAT), enter :kbd:`Y` for "yes"; otherwise enter :kbd:`N` for "no".

2. If you answered :kbd:`Y` because the host is behind NAT, you will be asked an additional configuration question:

   :guilabel:`External IP address for NAT`

   Enter the *publicly routable IP address of the NAT router*. This complements the other IP address you entered in :numref:`IP Address` (:ref:`IP Address`).

.. index:: configure-lockss; mail

-------------
Mail Settings
-------------

Mail Relay
==========

Prompt: :guilabel:`Mail relay for this machine`

Enter the hostname of the host's outgoing mail server, for example :samp:`smtp.myuniversity.edu`, or :samp:`localhost` if the host system is running a local mail daemon.

Mail Relay Credentials
======================

1. Prompt: :samp:`Does the mail relay {<mailhost>} need a username and password?`

   If the outgoing mail server requires password authentication, enter :kbd:`Y` for "yes"; otherwise, enter :kbd:`N` for "no".

2. If you answered :kbd:`Y` because the outgoing mail server requires password authentication, you will be asked additional configuration questions:

   a. Prompt: :samp:`User for {<mailhost>}`

      Enter the username for the mail server.

   b. Prompt: :samp:`Password for {<mailuser>}@{<mailhost>}`

      Enter the password for the username on the mail server.

   c. Prompt: :samp:`Password for {<mailuser>}@{<mailhost>} (again)`

      Re-enter the password for the username on the mail server. If the two passwords do not match, the password will be asked again.

Administrator Email
===================

Prompt: :guilabel:`E-mail address for administrator`

Enter the e-mail address of the person or team who will administer the LOCKSS node.

.. index:: configure-lockss; preservation network

-----------------------------
Preservation Network Settings
-----------------------------

Configuration URL
=================

1. Prompt: :guilabel:`Configuration URL`

   Enter the URL of your LOCKSS network's configuration file, for example :samp:`https://admin.mynetwork.org/lockss.xml`. This URL will be given to you by your LOCKSS network administrator. For example in the Global LOCKSS Network (GLN), this is ``https://props.lockss.org/daemon/lockss.xml``.

2. If the configuration URL begins with ``https:``, you will be asked additional configuration questions:

   a. Prompt: :guilabel:`Verify configuration server authenticity?`

      Enter :kbd:`Y` for "yes" if you would like to check the authenticity of the configuration server using a custom keystore; otherwise enter :kbd:`N` for "no".

   b. If you answered :kbd:`Y` because you would like to check the authenticity of the configuration server using a custom keystore, you will be asked an additional configuration question:

      :guilabel:`Server certificate keystore`

      Enter the path of a Java keystore used to verify the authenticity of the configuration server.

Configuration Proxy
===================

Prompt: :guilabel:`Configuration proxy (host:port)`

If the configuration URL can be reached directly, hit :kbd:`Enter` to leave this blank; otherwise, if a proxy server is required to reach the configuration URL, enter its host and port in :samp:`{host}:{port}` format (for example :samp:`proxy.myuniversity.edu:8888`).

Preservation Groups
===================

Prompt: :guilabel:`Preservation group(s), separated by ';'`

Enter a preservation group identifier (or a semicolon-separated list of preservation group identifiers). This will be given to you by your LOCKSS network administrator. For example in the Global LOCKSS Network (GLN), this is ``prod``.

.. index:: configure-lockss; Web user interface

---------------------------
Web User Interface Settings
---------------------------

1. Prompt: :guilabel:`User name for web UI administration`

   Enter a username for the primary administrative user in :term:`LOCKSS <LOCKSS stack>` Web user interfaces.

2. Prompt: :samp:`Password for web UI administration user {<uiuser>}`

   Enter a password for the primary administrative user.

3. Prompt: :samp:`Password for web UI administration user {<uiuser>} (again)`

   Re-enter the password for the primary administrative user. If the two passwords do not match, the password will be asked again.

Container Subnet
================

1. If :program:`configure-lockss` detects a discrepancy between a previously used subnet for inter-container communication in the system and the subnet it would choose now, you may either see the warning:

   :samp:`Container subnet has changed from {<former_subnet>} to {<new_subnet>}`

   or be asked the question:

   :samp:`Container subnet was {<former_subnet>}, we think it should now be {<new_subnet>}. Do you want to change it?`

   in which case you should enter :kbd:`Y` for "yes" (recommended), or :kbd:`N` for "no".

2. Prompt: :guilabel:`LOCKSS subnet for inter-service access control`

   Enter the subnet used for inter-container communication. We recommend accepting the proposed value by hitting :kbd:`Enter`.

.. index:: configure-lockss; storage areas

---------------------
Storage Area Settings
---------------------

The :term:`LOCKSS stack` needs several kinds of :term:`content storage` and :term:`operating storage`, as described in the :ref:`Storage Prerequisites` section. (See also important information about performance requirements for these storage areas in that section.)

Depending on your host system's layout, these storage areas may or may not be the same mount points or paths. Each path must be writable by the ``lockss`` user.

Subdirectories will be created in each storage area to fit the needs of each :doc:`stack component </introduction/components>`; for example :file:`lockss-stack-cfg-data` is the :ref:`LOCKSS Configuration Service`'s state data directory in the :term:`state data storage area`, and :file:`lockss-stack-repo-logs` is the :ref:`LOCKSS Repository Service`'s log directory in the :term:`log storage area`.

.. index:: content storage area; configuration

Content Storage Area Settings
=============================

1. Prompt: :guilabel:`Paths of the content storage areas, separated by ';'`

   Enter a semicolon-separated list of full paths of directories to be used as :term:`content storage areas <content storage area>`.

2. If the answer to the question is different than that from a previous configuration run, you will see the warning:

   ``Content storage areas have changed. Artifact reindexing may be needed; see manual.``

   This message indicates that changing the configured content storage areas may trigger the need for :term:`artifacts <artifact>` to be :index:`reindexed internally <artifact reindexing>`. This process happens in the background while the :term:`stack <LOCKSS stack>` runs but may take an extended period of time.

.. index:: state data storage area; configuration

State Data Storage Area Settings
================================

Prompt: :guilabel:`Path of the state data storage area`

Enter the desired path for the :term:`state data storage area`, which by default is the same as the *first* :term:`content storage area` (see :ref:`Content Storage Area Settings`).

.. index:: log storage area; configuration

Log Storage Area Settings
=========================

Prompt: :guilabel:`Path of the log storage area`

Enter the desired path for the :term:`log storage area`, which by default is the same as the :term:`state data storage area` (see :ref:`State Data Storage Area Settings`).

.. index:: temporary storage area; configuration

Temporary Storage Area Settings
===============================

Prompt: :guilabel:`Path of the temporary storage area`

Enter the desired path for the :term:`temporary storage area`, which by default is the same as the :term:`state data storage area` (see :ref:`State Data Storage Area Settings`).

.. index:: configure-lockss; database

-----------------
Database Settings
-----------------

For the :ref:`PostgreSQL` database, you have two options:

*  You can choose to use the :term:`LOCKSS stack`'s **embedded PostgreSQL database**, meaning a PostgreSQL database :term:`container` will be run and managed as part of the LOCKSS stack. This is the recommended option.

*  Alternatively, you can choose to use an **external PostgreSQL database**. Select this option if you wish to use an existing PostgreSQL database provisioned by your institution, or one that you run and manage yourself.

You will receive the following prompt:

:guilabel:`Use embedded LOCKSS PostgreSQL DB Service?`

*  To use the **embedded PostgreSQL database**, enter :kbd:`Y` for "yes", then follow the steps in the :ref:`embedded-postgresql-settings` section below.

*  To use an **external PostgreSQL database**, enter :kbd:`N` for "no", then follow the steps in the :ref:`external-postgresql-settings` section below.

.. tab-set::

   .. tab-item:: Embedded PostgreSQL Database
      :sync: embedded-postgresql
      :name: embedded-postgresql-settings

      Follow these steps if you entered :kbd:`Y` to use the **embedded PostgreSQL database**:

      1. Prompt: :guilabel:`Password for PostgreSQL database`

         Enter the password for the embedded PostgreSQL database.

         .. caution::

            This prompt is used to record the PostgreSQL database password in the LOCKSS stack's configuration. If you change the value of the PostgreSQL database password here without actually changing the PostgreSQL database password, the LOCKSS system components will no longer be able to connect to the PostgreSQL database. See :doc:`/appendix/postgresql` for details.

      2. Prompt: :guilabel:`Password for PostgreSQL database (again)`

         Re-enter the password for the embedded PostgreSQL database. If the two passwords do not match, the password will be asked again.

   .. tab-item:: External PostgreSQL Database
      :sync: external-postgresql
      :name: external-postgresql-settings

      Follow these steps if you entered :kbd:`N` to use an **external PostgreSQL database**:

      1. Prompt: :guilabel:`Fully qualified hostname (FQDN) of PostgreSQL host`

         Enter the hostname of the external PostgreSQL database, for example :samp:`postgres.myuniversity.edu`.

      2. Prompt: :guilabel:`Port used by PostgreSQL host`

         Enter the port where the external PostgreSQL database can be reached, for example :samp:`5432`.

      3. Prompt: :guilabel:`Schema for PostgreSQL database`

         Enter the schema name to be used by the LOCKSS system. The schema name used in the embedded PostgreSQL database is :samp:`LOCKSS`, but your database administrator may assign a different schema name to you.

      4. Prompt: :guilabel:`Database name prefix for PostgreSQL database`

         Enter the prefix to use for any LOCKSS-related database names in the schema. The database name prefix in the embedded PostgreSQL databse is :samp:`Lockss` (note the uppercase/lowercase), but your database administrator may assign a different database name prefix.

      5. Prompt: :guilabel:`Login name for PostgreSQL database`

         Enter the username for the external PostgreSQL database. The username in the embedded PostgreSQL database is :samp:`LOCKSS`, but your database administrator may assign a different username to you.

      6. Prompt: :guilabel:`Password for PostgreSQL database`

         Enter the password for the username in the external PostgreSQL database.

         .. caution::

            This prompt is used to record the PostgreSQL database password in the LOCKSS stack's configuration. If you change the value of the PostgreSQL database password here without actually changing the PostgreSQL database password, the LOCKSS system components will no longer be able to connect to the PostgreSQL database. Contact your PostgreSQL database administrator for details.

      7. Prompt: :guilabel:`Password for PostgreSQL database (again)`

         Re-enter the password for the username in the external PostgreSQL database. If the two passwords do not match, the password will be asked again.

.. index:: configure-lockss; stack components

------------------------
Stack Component Settings
------------------------

Crawler Service Settings
========================

1. Prompt: :guilabel:`Use LOCKSS Crawler Service?`

   Enter :kbd:`Y` for "yes" if you want the :ref:`LOCKSS Crawler Service` to be run as part of your :term:`LOCKSS stack`, otherwise enter :kbd:`N` for "no". (The only situation where a crawler service is not needed is LOCKSS networks that are exclusively using direct deposit to store content; most LOCKSS networks need the crawler service.)

2. If you answer :kbd:`Y` to the previous question, you will see these additional questions:

   a. Prompt: :guilabel:`Enable classic LOCKSS crawler?`

      Enter :kbd:`Y` for "yes" if you want to run the classic LOCKSS crawler, otherwise enter :kbd:`N` for "no". (Most LOCKSS networks using the crawler service use the classic LOCKSS crawler.)

   b. Prompt: :guilabel:`Enable Wget crawler?`

      Enter :kbd:`Y` for "yes" if you want to enable the usage of the external :term:`Wget` crawler, otherwise enter :kbd:`N` for "no".

Metadata Service Settings
=========================

Prompt: :guilabel:`Use LOCKSS Metadata Service?`

Enter :kbd:`Y` for "yes" if you want the :ref:`LOCKSS Metadata Service` to be run as part of your :term:`LOCKSS stack`, otherwise enter :kbd:`N` for "no".

SOAP Compatibility Service Settings
===================================

Prompt: :guilabel:`Use LOCKSS SOAP Compatibility Service?`

Enter :kbd:`Y` for "yes" if you want the :ref:`LOCKSS SOAP Compatibility Service` to be run as part of your :term:`LOCKSS stack`, otherwise enter :kbd:`N` for "no". (This is only needed if you have external tools using the LOCKSS' legacy SOAP Web Services.)

.. index:: configure-lockss; Web replay

-------------------
Web Replay Settings
-------------------

Pywb Settings
=============

Prompt: :guilabel:`Use LOCKSS Pywb Service?`

Enter :kbd:`Y` for "yes" to run :ref:`Pywb` as part of your :term:`LOCKSS stack`; otherwise, enter :kbd:`N` for "no".

OpenWayback Settings
====================

Prompt: :guilabel:`Use LOCKSS OpenWayback Service?`

Enter :kbd:`Y` for "yes" to run :ref:`OpenWayback` as part of your :term:`LOCKSS stack`; otherwise, enter :kbd:`N` for "no".

.. _final-steps-of-configure-lockss:

.. index:: configure-lockss; confirmation

------------------------------------------
Final Steps of :program:`configure-lockss`
------------------------------------------

1. Prompt: :guilabel:`OK to proceed?`

   Enter :kbd:`Y` for "yes" if the configuration values are to your liking; otherwise, enter :kbd:`N` for "no" to make edits.

2. If you answer :kbd:`Y` to accept the configuration values, :program:`configure-lockss` will perform the final configuration steps. You may be asked to confirm before directories are created for the first time:

   :samp:`{<directory>} does not exist; do you want to create it?`

   or before directory permissions are changed:

   :samp:`{<directory>} is not writable; do you want to make it writable?`

   In each case, enter :kbd:`Y` for "yes" and :kbd:`N` for "no".

   .. index:: configure-lockss; error condition

   .. admonition:: Error conditions and what to do about them

      During the process of creating directories or changing directory permissions, you may see the following types of error messages if an error occurs:

      :samp:`{<directory>} not writable by user {<user>}. Please make it so (check parent dir execute bits). LOCKSS will not run properly without it.`

      :samp:`Please create {<directory>} and make it writable by user {<user>}; LOCKSS will not run properly without it.`

      :samp:`{<directory>} still not writable by user {<user>}. Please make it so (check parent dir execute bits). LOCKSS will not run properly without it.`

      :samp:`Please ensure that {<directory>} is writable by user {<user>}; LOCKSS will not run properly without it.`

      The script will end with this warning:

      ``Storage directories have not been set up correctly. Either fix the ownership/permission problems then run scripts/configure-lockss -r, or re-run scripts/configure-lockss and specify different directories.``

      You can either fix any ownership and permission issues encountered and run ``scripts/configure-lockss --replay`` (or ``scripts/configure-lockss -r`` for short), or alternatively you can re-run ``scripts/configure-lockss`` but specify different directories.

----

.. rubric:: Footnotes

.. [#fn-hostconfig]

   If you have experience with LOCKSS 1.x, this is the equivalent of the :program:`hostconfig` script.
