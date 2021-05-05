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

--------
Hostname
--------

:guilabel:`Fully qualified hostname (FQDN) of this machine`

Enter the machine's fully-qualified hostname (meaning with its domain name), for example :samp:`locksstest.myuniversity.edu`.

----------
IP Address
----------

:guilabel:`IP address of this machine`

If the machine is publicly routable, meaning it has an IP address that can be used to identify it over the Internet, enter the publicly routable IP address. Otherwise, if the machine is accessible via network address translation (NAT), meaning it has an IP address that is valid only on your local network but it can be reached from the Internet via a NAT router, enter the internal IP address.

---------------------------
Network Address Translation
---------------------------

:guilabel:`Is this machine behind NAT?`

Select option A **or** option B:

A. If the machine is publicly routable, enter :kbd:`N`.

B. If the machine is not publicly routable but will be accessible via network address translation (NAT), enter :kbd:`Y`. You will then be asked an additional configuration question:

   1. :guilabel:`External IP address for NAT`

      Enter the publicly routable IP address of the NAT router.

-----------------
Initial UI Subnet
-----------------

:guilabel:`Initial subnet(s) for admin UI access`

Enter a semicolon-separated list of subnets in CIDR or mask notation that should initially have access to the Web user interfaces (UI) of the system. The access list can be modified later via the UI.

----------------
Container Subnet
----------------

1. *(Optional.)* If :program:`configure-lockss` detects a discrepancy between a previously used subnet for inter-container communication in the system and the subnet it would choose now, you may either see the warning:

   :guilabel:`Container subnet has changed from <former_subnet> to <new_subnet>`

   or be asked the question:

   :guilabel:`Container subnet was <former_subnet>, we think it should now be <new_subnet>. Do you want to change it?`

   in which case you should enter :kbd:`Y` (recommended) or :kbd:`N`.

2. :guilabel:`LOCKSS subnet for inter-service access control`

   Enter the subnet used for inter-container communication. We recommend accepting the proposed value by hitting :kbd:`Enter`.

---------
LCAP Port
---------

:guilabel:`LCAP V3 protocol port`

Enter the port on the publicly routable IP address that will be used to receive LCAP (LOCKSS polling and repair) traffic. Historically, most LOCKSS nodes use :samp:`9729`.

----------
Proxy Port
----------

:guilabel:`Proxy port`

Enter the port for the LOCKSS content proxy. We recommend accepting the default :samp:`24670`; the value can be changed later if necessary.

----------
Mail Relay
----------

:guilabel:`Mail relay for this machine`

Hostname of this machine's outgoing mail server, for example :samp:`smtp.myuniversity.edu`.

----------------------
Mail Relay Credentials
----------------------

:guilabel:`Does the mail relay <mailhost> need a username and password?`

Select option A **or** option B:

A. If the outgoing mail server does not require password authentication, enter :kbd:`N`.

B. If the outgoing mail server requires password authentication, enter :kbd:`Y`. You will then be asked additional configuration questions:

   1. :guilabel:`User for <mailhost>`

      Enter a username for the mail server.

   2. :guilabel:`Password for <mailuser>@<mailhost>`

      Enter the password for the username on the mail server.

   3. :guilabel:`Password for <mailuser>@<mailhost> (again)`

      Re-enter the password for the username on the mail server. If the two passwords do not match, the password will be asked again.

-------------------
Administrator Email
-------------------

:guilabel:`E-mail address for administrator`

Enter the e-mail address of the person or team who will administer the LOCKSS system on this machine.

-----------------
Configuration URL
-----------------

:guilabel:`Configuration URL`

Accept the default (:samp:`http://props.lockss.org:8001/demo/lockss.xml`) if you are not running your own LOCKSS network; otherwise, enter the URL of the LOCKSS network configuration file provided by your LOCKSS network administrator.

-------------------
Configuration Proxy
-------------------

:guilabel:`Configuration proxy (host:port)`

If the configuration URL can be reached directly, leave this blank; otherwise, if a proxy server is required to reach the configuration URL, enter its :samp:`{host}:{port}` (for example :samp:`proxy.myuniversity.edu:8080`).

------------------
Preservation Group
------------------

:guilabel:`Preservation group(s)`

Accept the default (:samp:`demo`) if you are not running your own LOCKSS network; otherwise, enter a semicolon-separated list of LOCKSS network identifiers as provided by your LOCKSS network administrator.

--------------------------------
Content Data Storage Directories
--------------------------------

1. :guilabel:`Root path for primary content data storage directories`

   Enter the full path of a directory to use as the root of the main storage area of the LOCKSS system. This is where preserved content will be stored, along with several databases; it is the analog of :file:`/cache0` in the classic LOCKSS system.

2. :guilabel:`Use additional directories for content data storage?`

   If you want to use more than one filesystem to store preserved content answer :kbd:`Y`.

   If you answer :kbd:`Y` to this question:

   *  :guilabel:`Enter root path $count to additional content storage directories (q to quit)`

      You will be prompted repeatedly for extra paths; enter one per line, then enter :kbd:`q` when done.

-----------------------
Service Log Directories
-----------------------

:guilabel:`Root path for service logs directories`

Defaults to the content data storage directory root. Enter a different path if you want to put the logs elsewhere. In the classic LOCKSS system this was :file:`/var/log/lockss`, but now there will be a set of subdirectories, one for each component service.

-----------------------------
Temporary Storage Directories
-----------------------------

:guilabel:`Root path for temporary storage directories (local storage preferred)`

Defaults to the content data storage directory root. If that directory is remote (e.g. NFS), performance can be improved by supplying a local disk directory here. Do not use a RAM-based ``tmpfs``; in some circumstances a substantial amount of temporary space (tens of GB) may be needed.

----------------------------
Install Script Log Directory
----------------------------

:guilabel:`Directory for storing install script logs`

Defaults to a directory under the content data storage directory root. Enter a directory where logging for ``lockss-installer``-related logging will be appended.

------------------
Web user interface
------------------

1. :guilabel:`User name for web UI administration`

   Enter a username for the primary administrative user in the LOCKSS system's Web user interfaces.

2. :guilabel:`Password for web UI administration user <uiuser>`

   Enter a password for the primary administrative user.

3. :guilabel:`Password for web UI administration user <uiuser> (again)`

   Re-enter the password for the primary administrative user (if the two passwords do not match, the password will be asked again).

----------------------
Metadata Query Service
----------------------

:guilabel:`Use LOCKSS Metadata Query Service?`

Enter :kbd:`Y` if you want the metadata query service to be run, otherwise :kbd:`N`.

---------------------------
Metadata Extraction Service
---------------------------

:guilabel:`Use LOCKSS Metadata Extractor Service?`

Enter :kbd:`Y` if you want the metadata extraction service to be run, otherwise :kbd:`N`.

----------
PostgreSQL
----------

.. |postgres-guilabel| replace:: :guilabel:`Use LOCKSS PostgreSQL DB Service?`

|postgres-guilabel|

Enter :kbd:`Y` to use the embedded PostgreSQL database (recommended in most cases), or :kbd:`N` if you wish to use an external PostgreSQL database.

*  Enter :kbd:`Y` to use the embedded PostgreSQL database (recommended in most cases). Complete the :ref:`Using the Embedded PostgreSQL Database` section next.

*  Enter :kbd:`N` if you wish to use your own external PostgreSQL database. Complete the :ref:`Using an External PostgreSQL Database` section next.

Using the Embedded PostgreSQL Database
======================================

.. note::

   Complete this section only if you answer :kbd:`Y` to |postgres-guilabel|.

1. :guilabel:`Password for PostgreSQL database`

   Enter a password for the embedded PostgreSQL database.

2. :guilabel:`Password for PostgreSQL database (again)`

   Re-enter the password for the PostgreSQL database (if the two passwords do not match, the password will be asked again).

3. Complete the :ref:`Solr` section next.

Using an External PostgreSQL Database
=====================================

.. note::

   Complete this section only if you answer :kbd:`N` to |postgres-guilabel|.

1. :guilabel:`Fully qualified hostname (FQDN) of PostgreSQL host`

   Enter the hostname of your PostgreSQL database, for example :samp:`mypgsql.myuniversity.edu`.

2. :guilabel:`Port used by PostgreSQL host`

   Enter the port where your running PostgreSQL database can be reached, for example :samp:`5432`.

3. :guilabel:`Login name for PostgreSQL service`

   Enter the user name for your PostgreSQL database. The default is :samp:`LOCKSS`.

4. :guilabel:`Schema for PostgreSQL service`

   Enter the schema name to be used by the LOCKSS system. The default is :samp:`LOCKSS`.

5. :guilabel:`Database name prefix for PostgreSQL service`

   Prefix to use for any LOCKSS databases. The default is :samp:`Lockss` (note the uppercase/lowercase).

6. :guilabel:`Password for PostgreSQL database`

   Enter the password for your PostgreSQL database.

7. :guilabel:`Password for PostgreSQL database (again)`

   Re-enter the password for your PostgreSQL database (if the two passwords do not match, the password will be asked again).

8. Complete the :ref:`Solr` section next.

----
Solr
----

:guilabel:`Use LOCKSS Solr Service?`

*  Enter :kbd:`Y` to use the embedded Solr server. This is recommended in most cases.

*  Enter :kbd:`N` to use your own external Solr database. If you answer :kbd:`N`, you will be prompted for the following information:

   1. :guilabel:`Fully qualified hostname (FQDN) of Solr host:`

   Enter the hostname of your Solr database server, for example :samp:`mysolr.myuniversity.edu`.

   2. :guilabel:`Port used by Solr host:`

   Enter the port where your running Solr database can be reached, for example :samp:`8983`.

   3. :guilabel:`Solr core repo name:`

   Enter name of the Solr core for the LOCKSS repository. The default is :samp:`lockss-repo`.

----
Pywb
----

:guilabel:`Use LOCKSS Pywb Service?:`

Enter :kbd:`Y` to run an embedded Pywb engine for Web replay, :kbd:`N` otherwise.

-----------
OpenWayback
-----------

1. :guilabel:`Use LOCKSS OpenWayback Service?:`

   Enter :kbd:`Y` to use an embedded OpenWayback engine for Web replay, :kbd:`N` otherwise.

2. :guilabel:`Okay to turn off authentication for read-only requests for LOCKSS Repository Service?:`

   OpenWayback currently does not supply user credentials when reading content from the LOCKSS repository, so the repository must be configured to respond to unauthenticated read requests. Enter :kbd:`Y` to accept this, otherwise OpenWayback will not be enabled.

----------
Conclusion
----------

:guilabel:`OK to store this configuration:`

Enter :kbd:`Y` if the configuration values are to your liking, otherwise :kbd:`N` to make edits.

If you enter :kbd:`Y`, some checks will be run, you may be prompted before the creation of necessary directories, and you will be prompted to run :program:`scripts/start-lockss` to start the configured system.
