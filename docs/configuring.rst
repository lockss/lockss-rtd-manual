=============================
Configuring the LOCKSS System
=============================

After `installing the LOCKSS system <installing>`_, configure the system with the :program:`configure-lockss` script:

.. code-block:: shell

   scripts/configure-lockss

If you have experience with classic LOCKSS daemon version 1.x, this is the equivalent of :program:`hostconfig`.

Some notes about using :program:`configure-lockss`:

*  When run the first time, some of the questions asked by the script will have a suggested or default value, displayed in square brackets; hit :kbd:`Enter` to accept the suggested value, or type the correct value and hit :kbd:`Enter`.

*  Any subsequent runs will use the previous values as the default value; review and hit :kbd:`Enter` to leave unchanged.

*  Password prompts will not display the previous value but can still be left unchanged with :kbd:`Enter`.

.. contents:: Chapter Overview
   :local:
   :depth: 1

----------------
Network Settings
----------------

Hostname
========

:guilabel:`Fully qualified hostname (FQDN) of this machine`

Enter the machine's fully-qualified hostname (meaning with its domain name), for example :samp:`locksstest.myuniversity.edu`.

IP Address
==========

:guilabel:`IP address of this machine`

If the machine is publicly routable, meaning it has an IP address that can be used to identify it over the Internet, enter the publicly routable IP address. Otherwise, if the machine is accessible via network address translation (NAT), meaning it has an IP address that is valid only on your local network but it can be reached from the Internet via a NAT router, enter the internal IP address.

Network Address Translation
===========================

1. :guilabel:`Is this machine behind NAT?`

   If the machine is publicly routable, enter :kbd:`N`; otherwise, if the machine is not publicly routable but will be accessible via network address translation (NAT), enter :kbd:`Y`.

2. If you answered :kbd:`Y`, you will be asked an additional configuration question:

   :guilabel:`External IP address for NAT`

   Enter the publicly routable IP address of the NAT router.

Initial UI Subnet
=================

:guilabel:`Initial subnet(s) for admin UI access`

Enter a semicolon-separated list of subnets in CIDR or mask notation that should initially have access to the Web user interfaces (UI) of the system. The access list can be modified later via the UI.

Container Subnet
================

1. If :program:`configure-lockss` detects a discrepancy between a previously used subnet for inter-container communication in the system and the subnet it would choose now, you may either see the warning:

   :guilabel:`Container subnet has changed from <former_subnet> to <new_subnet>`

   or be asked the question:

   :guilabel:`Container subnet was <former_subnet>, we think it should now be <new_subnet>. Do you want to change it?`

   in which case you should enter :kbd:`Y` (recommended) or :kbd:`N`.

2. :guilabel:`LOCKSS subnet for inter-service access control`

   Enter the subnet used for inter-container communication. We recommend accepting the proposed value by hitting :kbd:`Enter`.

LCAP Port
=========

:guilabel:`LCAP V3 protocol port`

Enter the port on the publicly routable IP address that will be used to receive LCAP (LOCKSS polling and repair) traffic. Historically, most LOCKSS nodes use :samp:`9729`.

-------------
Mail Settings
-------------

Mail Relay
==========

:guilabel:`Mail relay for this machine`

Hostname of this machine's outgoing mail server, for example :samp:`smtp.myuniversity.edu`.

Mail Relay Credentials
======================

1. :guilabel:`Does the mail relay <mailhost> need a username and password?`

   If the outgoing mail server does not require password authentication, enter :kbd:`N`; otherwise, enter :kbd:`Y`.

2. If you answered :kbd:`Y`, you will be asked additional configuration questions:

   1. :guilabel:`User for <mailhost>`

      Enter a username for the mail server.

   2. :guilabel:`Password for <mailuser>@<mailhost>`

      Enter the password for the username on the mail server.

   3. :guilabel:`Password for <mailuser>@<mailhost> (again)`

      Re-enter the password for the username on the mail server. If the two passwords do not match, the password will be asked again.

Administrator Email
===================

:guilabel:`E-mail address for administrator`

Enter the e-mail address of the person or team who will administer the LOCKSS system on this machine.

-----------------------------
Preservation Network Settings
-----------------------------

Configuration URL
=================

1. :guilabel:`Configuration URL`

   Accept the default (:samp:`http://props.lockss.org:8001/demo/lockss.xml`) if you are not running your own LOCKSS network; otherwise, enter the URL of the LOCKSS network configuration file provided by your LOCKSS network administrator.

2. If the configuration URL begins with ``https:``, you will be asked additional configuration questions:

   1. :guilabel:`Verify configuration server authenticity?`

      Enter :kbd:`Y` if you would like to check the authenticity of the configuration server using a custom keystore; otherwise enter :kbd:`N`.

   2. If you answered :kbd:`Y`, you will be asked an additional configuration question:

      :guilabel:`Server certificate keystore`

      Enter the path of a Java keystore used to vverify the authenticity of the configuration server.

Configuration Proxy
===================

:guilabel:`Configuration proxy (host:port)`

If the configuration URL can be reached directly, leave this blank; otherwise, if a proxy server is required to reach the configuration URL, enter its host and port in :samp:`{host}:{port}` format (for example :samp:`proxy.myuniversity.edu:8080`).

Preservation Groups
===================

:guilabel:`Preservation group(s)`

Accept the default (:samp:`demo`) if you are not running your own LOCKSS network; otherwise, enter a semicolon-separated list of LOCKSS network identifiers as provided by your LOCKSS network administrator, for example :samp:`ournetwork` or :samp:`prod;usdocspln`.

----------------
Storage Settings
----------------

Content Data Storage Directories
================================

1. :guilabel:`Root path for primary content data storage directories`

   Enter the full path of a directory to use as the root of the main storage area of the LOCKSS system, where preserved content will be stored along with several databases. It is the analog of :file:`/cache0` in the classic LOCKSS system.

2. :guilabel:`Use additional directories for content data storage?`

   If you want to use more than one filesystem to store preserved content, enter :kbd:`Y`; otherwise, enter :kbd:`N`.

3. If you answered :kbd:`Y`, you will be asked an additional configuration question:

   :guilabel:`Enter root path $count to additional content storage directories (q to quit)`

   Enter one additional directory per line, then enter :kbd:`q` when done.

Service Log Directories
=======================

:guilabel:`Root path for service logs directories`

This directory is used as the root of the storage area for log files in the LOCKSS system. Accept the default (same directory as the content data storage directory root) by hitting :kbd:`Enter`, or enter a custom path.

Temporary Storage Directories
=============================

:guilabel:`Root path for temporary storage directories (local storage preferred)`

This directory is used as the root of the storage area for temporary files in the LOCKSS system. Accept the default (same directory as the content data storage directory root) by hitting :kbd:`Enter`, or enter a custom path.

.. tip::

   If this directory is remote (e.g. NFS), performance can be improved by supplying a local directory here.

.. caution::

   Depending on the characteristics of the preservation activities undertaken by the system, in some circumstances content processing may require a substantial amount of temporary space, up to tens of gigabytes. Do not use a RAM-based ``tmpfs`` volume, or a directory in a space-constrained partition.

Script Log Directory
====================

:guilabel:`Directory for storing install script logs`

This directory is used to store log files produced by :program:`lockss-installer` scripts. Accept the default (a directory under the content data storage directory root) by hitting :kbd:`Enter`, or enter a custom path.

---------------------------
Web User Interface Settings
---------------------------

1. :guilabel:`User name for web UI administration`

   Enter a username for the primary administrative user in the LOCKSS system's Web user interfaces.

2. :guilabel:`Password for web UI administration user <uiuser>`

   Enter a password for the primary administrative user.

3. :guilabel:`Password for web UI administration user <uiuser> (again)`

   Re-enter the password for the primary administrative user. If the two passwords do not match, the password will be asked again.

-----------------
Database Settings
-----------------

PostgreSQL
==========

:guilabel:`Use embedded LOCKSS PostgreSQL DB Service?`

Select **either** option A **or** option B:

A. Enter :kbd:`Y` to use the **embedded PostgreSQL database**. This is recommended in most cases; a PostgreSQL database will be run and managed by the LOCKSS system internally. If you choose this option, see :ref:`Embedded PostgreSQL Database`.

B. Enter :kbd:`N` to use an **external PostgreSQL database**. Select this option if you wish to use an existing PostgreSQL database at your institution or one that you run and manage yourself. If you choose this option, see :ref:`External PostgreSQL Database`.

Embedded PostgreSQL Database
----------------------------

If you select this option, you will be asked additional configuration questions:

1. :guilabel:`Password for PostgreSQL database`

   Enter the password for the embedded PostgreSQL database.

2. :guilabel:`Password for PostgreSQL database (again)`

   Re-enter the password for the embedded PostgreSQL database. If the two passwords do not match, the password will be asked again.

3. Complete the :ref:`Solr` section next.

External PostgreSQL Database
----------------------------

If you select this option, you will be asked additional configuration questions:

1. :guilabel:`Fully qualified hostname (FQDN) of PostgreSQL host`

   Enter the hostname of the external PostgreSQL database, for example :samp:`postgres.myuniversity.edu`.

2. :guilabel:`Port used by PostgreSQL host`

   Enter the port where the external PostgreSQL database can be reached, for example :samp:`5432`.

3. :guilabel:`Schema for PostgreSQL service`

   Enter the schema name to be used by the LOCKSS system. The schema name used in the embedded PostgreSQL database is :samp:`LOCKSS`, but your database administrator may assign a different schema name to you.

4. :guilabel:`Database name prefix for PostgreSQL service`

   Enter the prefix to use for any LOCKSS-related database names in the schema. The database name prefix in the embedded PostgreSQL databse is :samp:`Lockss` (note the uppercase/lowercase), but your database administrator may assign a different database name prefix.

5. :guilabel:`Login name for PostgreSQL service`

   Enter the username for the external PostgreSQL database. The username in the embedded PostgreSQL database is :samp:`LOCKSS`, but your database administrator may assign a different username to you.

6. :guilabel:`Password for PostgreSQL database`

   Enter the password for the username in the external PostgreSQL database.

7. :guilabel:`Password for PostgreSQL database (again)`

   Re-enter the password for the username in the external PostgreSQL database. If the two passwords do not match, the password will be asked again.

8. Complete the :ref:`Solr` section next.

Solr
====

:guilabel:`Use embedded LOCKSS Solr Service?`

Select **either** option A **or** option B:

A. Enter :kbd:`Y` to use the **embedded Solr database**. This is recommended in most cases; a Solr database will be run and managed by the LOCKSS system internally. If you choose this option, see :ref:`Embedded Solr Database`.

B. Enter :kbd:`N` to use an **external Solr database**. Select this option if you wish to use an existing Solr database at your institution or one that you run and manage yourself. If you choose this option, see :ref:`External Solr Database`.

Embedded Solr Database
----------------------

If you select this option, you will be asked additional configuration questions:

1. :guilabel:`User name for LOCKSS Solr access`

   Enter the username for the embedded Solr database.

2. :guilabel:`Password for LOCKSS Solr access`

   Enter the password for the username in the embedded Solr database.

3. :guilabel:`Password for LOCKSS Solr access (again)`

   Re-enter the password for the username in the embedded Solr database. If the two passwords do not match, the password will be asked again.

4. Complete the :ref:`Metadata Query Service` section next.

External Solr Database
----------------------

If you select this option, you will be asked additional configuration questions:

1. :guilabel:`Fully qualified hostname (FQDN) of Solr host`

   Enter the hostname of the external Solr database server, for example :samp:`solr.myuniversity.edu`.

2. :guilabel:`Port used by Solr host:`

   Enter the port used by the database server on the Solr host, for example :samp:`8983`.

3. :guilabel:`Solr core repo name:`

   Enter name of the Solr core for the LOCKSS repository. The Solr core name used in the embedded Solr database is :samp:`lockss-repo`, but your database administrator may assign a different Solr core name.

4. :guilabel:`User name for LOCKSS Solr access`

   Enter the username for the external Solr database.

5. :guilabel:`Password for LOCKSS Solr access`

   Enter the password for the username in the external Solr database.

6. :guilabel:`Password for LOCKSS Solr access (again)`

   Re-enter the password for the username in the external Solr database. If the two passwords do not match, the password will be asked again.

7. Complete the :ref:`Metadata Query Service` section next.

---------------
LOCKSS Services
---------------

Metadata Query Service
======================

:guilabel:`Use LOCKSS Metadata Query Service?`

Enter :kbd:`Y` if you want the metadata query service to be run, otherwise :kbd:`N`.

Metadata Extraction Service
===========================

:guilabel:`Use LOCKSS Metadata Extraction Service?`

Enter :kbd:`Y` if you want the metadata extraction service to be run, otherwise :kbd:`N`.

-------------------
Web Replay Settings
-------------------

Pywb
====

:guilabel:`Use LOCKSS Pywb Service?`

Enter :kbd:`Y` to run an embedded Pywb engine for Web replay; otherwise, enter :kbd:`N`.

OpenWayback
===========

1. :guilabel:`Use LOCKSS OpenWayback Service?`

   Enter :kbd:`Y` to use an embedded OpenWayback engine for Web replay; otherwise, enter :kbd:`N`.

2. If you answered :kbd:`Y`, you will be asked an additional configuration question:

   :guilabel:`Okay to turn off authentication for read-only requests for LOCKSS Repository Service?`

   OpenWayback currently does not supply user credentials when reading content from the LOCKSS repository, so the repository must be configured to respond to unauthenticated read requests. Enter :kbd:`Y` to accept this, otherwise you will see the warning:

   :guilabel:`Not enabling OpenWayback Service`

   and OpenWayback will not be run.

-----------
Final Steps
-----------

1. :guilabel:`OK to store this configuration?`

  Enter :kbd:`Y` if the configuration values are to your liking; otherwise, enter :kbd:`N` to make edits.

2. If you answer :kbd:`Y`, :program:`configure-lockss` will perform the final configuration steps. You may be asked to confirm before directories are created for the first time:

   :guilabel:`<directory> does not exist; shall I create it?`

   or before directory permissions are changed:

   :guilabel:`<directory> is not writable; shall I chown it?`

   In each case, enter :kbd:`Y` for "yes" and :kbd:`N` for "no".
