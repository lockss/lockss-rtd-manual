=============================
Configuring the LOCKSS System
=============================

After `installing the LOCKSS system <installing>`_, you will configure it with the :program:`configure-lockss` script. If you have experience with classic LOCKSS daemon version 1.x, this is the equivalent of :program:`hostconfig`.

-------------------------------------------
Before Invoking :program:`configure-lockss`
-------------------------------------------

You will need to gather information to answer configuration questions asked by :program:`configure-lockss`, including:

*  The name (FQDN) of the host, the IP address of the host, and if behind NAT, the external IP address for NAT.

*  The mail relay host, and optionally mail credentials, for sending e-mail from the host, and the e-mail address for the administrator of the system.

*  The configuration URL and preservation group or groups corresponding to the LOCKSS network your system is joining.

*  The paths for the primary content storage area, any additional content storage areas, the data storage area, the temporary storage area, and the log storage area.

   Each of these paths needs to be writeable by the ``lockss`` user. If this is not the case, set them up as ``root`` before running :program:`configure-lockss`.

*  Username and password for the Web user interfaces.

*  A password for the PostgreSQL database.

   *  Alternatively, if using an existing PostgreSQL database, the host name, port, schema, username and password for the external PostgreSQL database, as well as a prefix for database names.

*  A username and password for the Solr database.

   *  Alternatively, if using an existing Solr database, the host name, port, username and password for the external Solr database, as well as the core name for the LOCKSS repository.

*  Whether you wish to use the LOCKSS Crawler Service, LOCKSS Metadata Extraction Service, LOCKSS Metadata Service, LOCKSS SOAP Compatibility Service, Pywb Web replay engine, and OpenWayback Web replay engine.

Some notes about using :program:`configure-lockss`:

*  When run the first time, some of the questions asked by the script will have a suggested or default value, displayed in square brackets; hit :kbd:`Enter` to accept the suggested value, or type the correct value and hit :kbd:`Enter`.

*  Any subsequent runs will use the previous values as the default value; review and hit :kbd:`Enter` to leave unchanged.

*  Password prompts will not display the previous value but can still be left unchanged with :kbd:`Enter`.

------------------------------------
Invoking :program:`configure-lockss`
------------------------------------

To invoke :program:`configure-lockss`, simply run this command in the ``lockss`` user's :file:`lockss-installer` directory as ``lockss`` [#fnlockss]_:

.. code-block:: shell

   scripts/configure-lockss

The script will begin with the first series of configuration questions, about :ref:`Kubernetes Settings`.

-------------------
Kubernetes Settings
-------------------

Prompt: :guilabel:`Command to use to execute kubectl commands`

Enter the command to invoke :program:`kubectl` in your environment. If you are using the K3s Kubernetes environment that ships with the LOCKSS system, the proposed value is already correct.

.. FIXME the script can exit here if the K8s (sic) config file can't be written to

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

If the machine is publicly routable, meaning it has an IP address that can be used to identify it over the Internet, enter the publicly routable IP address. Otherwise, if the machine is accessible via network address translation (NAT), meaning it has an IP address that is valid only on your local network but it can be reached from the Internet via a NAT router, enter the internal IP address.

Network Address Translation
===========================

1. Prompt: :guilabel:`Is this machine behind NAT?`

   If the machine is publicly routable, enter :kbd:`N`; otherwise, if the machine is not publicly routable but will be accessible via network address translation (NAT), enter :kbd:`Y`.

2. If you answered :kbd:`Y`, you will be asked an additional configuration question:

   :guilabel:`External IP address for NAT`

   Enter the publicly routable IP address of the NAT router.

Initial UI Subnet
=================

Prompt: :guilabel:`Initial subnet(s) for admin UI access`

Enter a semicolon-separated list of subnets in CIDR or mask notation that should initially have access to the Web user interfaces (UI) of the system. The access list can be modified later via the UI.

Container Subnet
================

1. If :program:`configure-lockss` detects a discrepancy between a previously used subnet for inter-container communication in the system and the subnet it would choose now, you may either see the warning:

   :guilabel:`Container subnet has changed from <former_subnet> to <new_subnet>`

   or be asked the question:

   :guilabel:`Container subnet was <former_subnet>, we think it should now be <new_subnet>. Do you want to change it?`

   in which case you should enter :kbd:`Y` (recommended) or :kbd:`N`.

2. Prompt: :guilabel:`LOCKSS subnet for inter-service access control`

   Enter the subnet used for inter-container communication. We recommend accepting the proposed value by hitting :kbd:`Enter`.

LCAP Port
=========

Prompt: :guilabel:`LCAP V3 protocol port`

Enter the port on the publicly routable IP address that will be used to receive LCAP (LOCKSS polling and repair) traffic. Historically, most LOCKSS nodes use :samp:`9729`.

-------------
Mail Settings
-------------

Mail Relay
==========

Prompt: :guilabel:`Mail relay for this machine`

Enter the hostname of this machine's outgoing mail server, for example :samp:`smtp.myuniversity.edu`.

Mail Relay Credentials
======================

1. Prompt: :guilabel:`Does the mail relay <mailhost> need a username and password?`

   If the outgoing mail server does not require password authentication, enter :kbd:`N`; otherwise, enter :kbd:`Y`.

2. If you answered :kbd:`Y`, you will be asked additional configuration questions:

   1. Prompt: :guilabel:`User for <mailhost>`

      Enter a username for the mail server.

   2. Prompt: :guilabel:`Password for <mailuser>@<mailhost>`

      Enter the password for the username on the mail server.

   3. Prompt: :guilabel:`Password for <mailuser>@<mailhost> (again)`

      Re-enter the password for the username on the mail server. If the two passwords do not match, the password will be asked again.

Administrator Email
===================

Prompt: :guilabel:`E-mail address for administrator`

Enter the e-mail address of the person or team who will administer the LOCKSS system on this machine.

-----------------------------
Preservation Network Settings
-----------------------------

Configuration URL
=================

1. Prompt: :guilabel:`Configuration URL`

   Accept the default (:samp:`http://props.lockss.org:8001/demo/lockss.xml`) if you are not running your own LOCKSS network; otherwise, enter the URL of the LOCKSS network configuration file provided by your LOCKSS network administrator.

2. If the configuration URL begins with ``https:``, you will be asked additional configuration questions:

   1. Prompt: :guilabel:`Verify configuration server authenticity?`

      Enter :kbd:`Y` if you would like to check the authenticity of the configuration server using a custom keystore; otherwise enter :kbd:`N`.

   2. If you answered :kbd:`Y`, you will be asked an additional configuration question:

      :guilabel:`Server certificate keystore`

      Enter the path of a Java keystore used to verify the authenticity of the configuration server.

Configuration Proxy
===================

Prompt: :guilabel:`Configuration proxy (host:port)`

If the configuration URL can be reached directly, leave this blank; otherwise, if a proxy server is required to reach the configuration URL, enter its host and port in :samp:`{host}:{port}` format (for example :samp:`proxy.myuniversity.edu:8080`).

Preservation Groups
===================

Prompt: :guilabel:`Preservation group(s)`

If you are setting up a test box in the Global LOCKSS Network, enter :samp:`demoprod`. If you are setting up a test box in a private LOCKSS network, enter a semicolon-separated list of LOCKSS network identifiers as provided by your LOCKSS network administrator, for example :samp:`ournetwork` or :samp:`prod;usdocspln`. Otherwise, accept the default (:samp:`demo`).

-------------
Storage Areas
-------------

The LOCKSS system needs several kinds of storage areas, as described in the :ref:`Storage` section.

Depending on your host system's layout, these storage areas may all be the same, or all be different mount points or paths. Each path must be writeable by the ``lockss`` user.

Subdirectories will be created in each storage area to fit the needs of each system component; for example :file:`lockss-stack-cfg-data` is the LOCKSS configuration service's data directory in the data storage area, and :file:`lockss-stack-repo-logs` is the LOCKSS repository service's log directory in the log storage area.

Data Storage Area
=================

Prompt: :guilabel:`Root path for data storage`

This directory is used as the root of the storage area for databases and other state files. Enter the desired path, or hit :kbd:`Enter` to accept a previously-entered value (if re-configuring).

Content Storage Areas
=====================

1. Prompt: :guilabel:`Root path(s) for content storage`

   Enter a semicolon-separated list of full paths of directories to be used to store preserved content.

2. If the answer to the question is different than that from a previous configuration run, you will see the warning:

   ``If you have removed or reordered content storage directories, you must run scripts/reindex-artifacts``

   If you have done anything other add new content storage areas to the end of the previously-entered value, you must run ``scripts/reindex-artifacts`` after completion of :program:`configure-lockss`, before starting the system.

Log Storage Area
================

Prompt: :guilabel:`Root path for log storage`

This directory is used as the root of the storage area for log files in the LOCKSS system. Accept the default (same directory as the content data storage directory root) by hitting :kbd:`Enter`, or enter a custom path.

Temporary Storage Area
======================

Prompt: :guilabel:`Root path for temporary storage (local storage preferred)`

This directory is used as the root of the storage area for temporary files in the LOCKSS system. Accept the default (same directory as the content data storage directory root) by hitting :kbd:`Enter`, or enter a custom path.

.. tip::

   The LOCKSS software makes heavy use of temporary storage, and we recommend that temporary directories be placed on a filesystem with relatively low latency. If the content data storage directories are on network storage (for example NFS), system performance may be improved by supplying a local directory for temporary data storage.

.. caution::

   Depending on the characteristics of the preservation activities undertaken by the system, in some circumstances content processing may require a substantial amount of temporary space, up to tens of gigabytes. Do not use a RAM-based ``tmpfs`` volume, or a directory in a space-constrained partition.

---------------------------
Web User Interface Settings
---------------------------

1. Prompt: :guilabel:`User name for web UI administration`

   Enter a username for the primary administrative user in the LOCKSS system's Web user interfaces.

2. Prompt: :guilabel:`Password for web UI administration user <uiuser>`

   Enter a password for the primary administrative user.

3. Prompt: :guilabel:`Password for web UI administration user <uiuser> (again)`

   Re-enter the password for the primary administrative user. If the two passwords do not match, the password will be asked again.

-----------------
Database Settings
-----------------

PostgreSQL
==========

Prompt: :guilabel:`Use embedded LOCKSS PostgreSQL DB Service?`

Select **either** option A **or** option B:

A. Enter :kbd:`Y` to use the **embedded PostgreSQL database**. This is recommended in most cases; a PostgreSQL database will be run and managed by the LOCKSS system internally. If you choose this option, see :ref:`Embedded PostgreSQL Database`.

B. Enter :kbd:`N` to use an **external PostgreSQL database**. Select this option if you wish to use an existing PostgreSQL database at your institution or one that you run and manage yourself. If you choose this option, see :ref:`External PostgreSQL Database`.

Embedded PostgreSQL Database
----------------------------

If you select this option, you will be asked additional configuration questions:

1. Prompt: :guilabel:`Password for PostgreSQL database`

   Enter the password for the embedded PostgreSQL database.

   .. warning::

      This prompt is used to record the PostgreSQL database password in the LOCKSS system's configuration. If you change the value of the PostgreSQL database password here without actually changing the PostgreSQL database password, the LOCKSS system components will no longer be able to connect to the PostgreSQL database. See :doc:`/appendix/postgresql` for details.

2. Prompt: :guilabel:`Password for PostgreSQL database (again)`

   Re-enter the password for the embedded PostgreSQL database. If the two passwords do not match, the password will be asked again.

3. Complete the :ref:`Solr` section next.

External PostgreSQL Database
----------------------------

If you select this option, you will be asked additional configuration questions:

1. Prompt: :guilabel:`Fully qualified hostname (FQDN) of PostgreSQL host`

   Enter the hostname of the external PostgreSQL database, for example :samp:`postgres.myuniversity.edu`.

2. Prompt: :guilabel:`Port used by PostgreSQL host`

   Enter the port where the external PostgreSQL database can be reached, for example :samp:`5432`.

3. Prompt: :guilabel:`Schema for PostgreSQL service`

   Enter the schema name to be used by the LOCKSS system. The schema name used in the embedded PostgreSQL database is :samp:`LOCKSS`, but your database administrator may assign a different schema name to you.

4. Prompt: :guilabel:`Database name prefix for PostgreSQL service`

   Enter the prefix to use for any LOCKSS-related database names in the schema. The database name prefix in the embedded PostgreSQL databse is :samp:`Lockss` (note the uppercase/lowercase), but your database administrator may assign a different database name prefix.

5. Prompt: :guilabel:`Login name for PostgreSQL service`

   Enter the username for the external PostgreSQL database. The username in the embedded PostgreSQL database is :samp:`LOCKSS`, but your database administrator may assign a different username to you.

6. Prompt: :guilabel:`Password for PostgreSQL database`

   Enter the password for the username in the external PostgreSQL database.

   .. warning::

      This prompt is used to record the PostgreSQL database password in the LOCKSS system's configuration. If you change the value of the PostgreSQL database password here without actually changing the PostgreSQL database password, the LOCKSS system components will no longer be able to connect to the PostgreSQL database. Contact your PostgreSQL database administrator for details.

7. Prompt: :guilabel:`Password for PostgreSQL database (again)`

   Re-enter the password for the username in the external PostgreSQL database. If the two passwords do not match, the password will be asked again.

8. Complete the :ref:`Solr` section next.

Solr
====

Prompt: :guilabel:`Use embedded LOCKSS Solr Service?`

Select **either** option A **or** option B:

A. Enter :kbd:`Y` to use the **embedded Solr database**. This is recommended in most cases; a Solr database will be run and managed by the LOCKSS system internally. If you choose this option, see :ref:`Embedded Solr Database`.

B. Enter :kbd:`N` to use an **external Solr database**. Select this option if you wish to use an existing Solr database at your institution or one that you run and manage yourself. If you choose this option, see :ref:`External Solr Database`.

Embedded Solr Database
----------------------

If you select this option, you will be asked additional configuration questions:

1. Prompt: :guilabel:`User name for LOCKSS Solr access`

   Enter the username for the embedded Solr database.

2. Prompt: :guilabel:`Password for LOCKSS Solr access`

   Enter the password for the username in the embedded Solr database.

3. Prompt: :guilabel:`Password for LOCKSS Solr access (again)`

   Re-enter the password for the username in the embedded Solr database. If the two passwords do not match, the password will be asked again.

4. Complete the :ref:`Metadata Query Service` section next.

External Solr Database
----------------------

If you select this option, you will be asked additional configuration questions:

1. Prompt: :guilabel:`Fully qualified hostname (FQDN) of Solr host`

   Enter the hostname of the external Solr database server, for example :samp:`solr.myuniversity.edu`.

2. Prompt: :guilabel:`Port used by Solr host:`

   Enter the port used by the database server on the Solr host, for example :samp:`8983`.

3. Prompt: :guilabel:`Solr core repo name:`

   Enter name of the Solr core for the LOCKSS repository. The Solr core name used in the embedded Solr database is :samp:`lockss-repo`, but your database administrator may assign a different Solr core name.

4. Prompt: :guilabel:`User name for LOCKSS Solr access`

   Enter the username for the external Solr database.

5. Prompt: :guilabel:`Password for LOCKSS Solr access`

   Enter the password for the username in the external Solr database.

6. Prompt: :guilabel:`Password for LOCKSS Solr access (again)`

   Re-enter the password for the username in the external Solr database. If the two passwords do not match, the password will be asked again.

7. Complete the :ref:`Metadata Query Service` section next.

---------------
LOCKSS Services
---------------

Metadata Query Service
======================

Prompt: :guilabel:`Use LOCKSS Metadata Query Service?`

Enter :kbd:`Y` if you want the metadata query service to be run, otherwise :kbd:`N`.

Metadata Extraction Service
===========================

Prompt: :guilabel:`Use LOCKSS Metadata Extraction Service?`

Enter :kbd:`Y` if you want the metadata extraction service to be run, otherwise :kbd:`N`.

SOAP Compatibility Service
==========================

Prompt: :guilabel:`Use LOCKSS SOAP Compatibility Service?`

Enter :kbd:`Y` if you want the SOAP compatibility servvice to be run, otherwise :kbd:`N`.

-------------------
Web Replay Settings
-------------------

Pywb
====

Prompt: :guilabel:`Use LOCKSS Pywb Service?`

Enter :kbd:`Y` to run an embedded Pywb engine for Web replay; otherwise, enter :kbd:`N`.

OpenWayback
===========

1. Prompt: :guilabel:`Use LOCKSS OpenWayback Service?`

   Enter :kbd:`Y` to use an embedded OpenWayback engine for Web replay; otherwise, enter :kbd:`N`.

2. If you answered :kbd:`Y`, you will be asked an additional configuration question:

   :guilabel:`Okay to turn off authentication for read-only requests for LOCKSS Repository Service?`

   OpenWayback currently does not supply user credentials when reading content from the LOCKSS repository, so the repository must be configured to respond to unauthenticated read requests. Enter :kbd:`Y` to accept this, otherwise you will see the warning:

   :guilabel:`Not enabling OpenWayback Service`

   and OpenWayback will not be run.

-----------
Final Steps
-----------

1. Prompt: :guilabel:`OK to store this configuration?`

  Enter :kbd:`Y` if the configuration values are to your liking; otherwise, enter :kbd:`N` to make edits.

2. If you answer :kbd:`Y`, :program:`configure-lockss` will perform the final configuration steps. You may be asked to confirm before directories are created for the first time:

   :guilabel:`<directory> does not exist; shall I create it?`

   or before directory permissions are changed:

   :guilabel:`<directory> is not writable; shall I chown it?`

   In each case, enter :kbd:`Y` for "yes" and :kbd:`N` for "no".

----

.. rubric:: Footnotes

.. [#fnlockss]

   See :doc:`/sysadmin/lockss`.
