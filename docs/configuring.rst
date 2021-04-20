=============================
Configuring the LOCKSS System
=============================

After `installing the LOCKSS system <installing>`_, configure the system with the :program:`scripts/configure-lockss` script:

.. code-block:: shell

   scripts/configure-lockss

(If you have experience with classic LOCKSS daemon version 1.x, this is the equivalent of :program:`hostconfig`.)

When run the first time, some of the questions asked by the script will have a suggested or default value, displayed in square brackets; hit :kbd:`Enter` to accept the suggested value, or type the correct value and hit :kbd:`Enter`. Any subsequent runs will use the previous values as the default value; review and hit :kbd:`Enter` to leave unchanged. Password prompts will not display the previous value but can still be left unchanged with :kbd:`Enter`.

--------
Hostname
--------

:guilabel:`Fully qualified hostname (FQDN) of this machine:`

Enter the machine's hostname, for example :samp:`locksstest.myuniversity.edu`.

----------
IP Address
----------

:guilabel:`IP address of this machine:`

Enter the publicly routable IP address of the machine, or if it is not publicly routable but will be accessible via network address translation (NAT), its IP address on the internal network.

---------------------------
Network Address Translation
---------------------------

:guilabel:`Is this machine behind NAT?:`

Enter :kbd:`Y` if the machine is not publicly routable but will be accessible via network address translation (NAT), or :kbd:`N` otherwise.

*  :guilabel:`External IP address for NAT:`

   If you answer :kbd:`Y` to the previous question, enter the publicly routable IP address of the NAT router.

--------------
Initial Subnet
--------------

:guilabel:`Initial subnet for admin UI access:`

Enter a semicolon-separated list of subnets in CIDR or mask notation that should initially have access to the Web user interfaces of the system. The access list can be modified later via the UI.

*FIXME*

5.  ``LOCKSS subnet for container access:`` This is calculated from the MicroK8s node and should not need to be modified in a standard installation.

---------
LCAP Port
---------

:guilabel:`LCAP V3 protocol port:`

Enter the port on the publicly routable IP address that will be used to receive LCAP (LOCKSS polling and repair) traffic. Historically, most LOCKSS nodes use :samp:`9729`.

----------
Proxy Port
----------

:guilabel:`PROXY port:`

Port for the LOCKSS content proxy. Accept the default -- it can be changed later if necessary.

----------
Mail Relay
----------

:guilabel:`Mail relay for this machine:`

Hostname of this machine's outgoing mail server.

----------------------
Mail Relay Credentials
----------------------

:guilabel:`Does mail relay <mailhost> need user & password`

Enter :kbd:`Y` if the outgoing mail server requires password authentication, :kbd:`N` otherwise.

If you answer :kbd:`Y` to this question, you will be prompted for the following information:

   1. :guilabel:`User for <mailhost>:`

      Enter the username for the mail server.

   2. :guilabel:`Password for <mailuser>@<mailhost>:`

      Enter the password for the given username.

   3. :guilabel:`Password for <mailuser>@<mailhost> (again):`

   Re-enter the mail server password (if the two passwords do not match, the password will be asked again).

-------------------
Administrator Email
-------------------

:guilabel:`E-mail address for administrator:`

Enter the e-mail address of the person or team who will administer the LOCKSS system on this machine.

-----------------
Configuration URL
-----------------

:guilabel:`Configuration URL:`

Enter the URL of the LOCKSS network configuration file. If you are not running your own LOCKSS network, use :samp:`http://props.lockss.org:8001/demo/lockss.xml`, the configuration file for a demo network set up for LOCKSS 2.0 pre-release testing.

-------------------
Configuration Proxy
-------------------

:guilabel:`Configuration proxy (host:port):`

If a proxy server is required to reach the configuration server, enter its :samp:`{host}:{port}` here, otherwise leave this blank.

------------------
Preservation Group
------------------

:guilabel:`Preservation group(s):`

Enter a semicolon-separated list of preservation network identifiers. If you are not joining an existing network or running your own, enter :samp:`demo`, the network identifier for the demo network set up for LOCKSS 2.0 pre-release testing.

-------------------------
Content Storage Directory
-------------------------

:guilabel:`Content data storage directory:`

Enter the full path of a directory to use as the root of the main storage area of the LOCKSS system. This is where preserved content will be stored, along with several databases; it is the analog of :file:`/cache0` in the classic LOCKSS system.

--------------------------------------
Additional Content Storage Directories
--------------------------------------

:guilabel:`Use additional directories for content storage?:`

If you want to use more than one filesystem to store preserved content answer :kbd:`Y`.

If you answer :kbd:`Y` to this question:

*  :guilabel:`Enter path to additional content storage directory <n> (q to quit):`

   You will be prompted repeatedly for extra paths; enter one per line, then enter :kbd:`q` when done.

---------------------
Service Log Directory
---------------------

:guilabel:`Service logs directory:`

Defaults to the content data storage directory; enter a different path if you want to put the logs elsewhere. In the classic LOCKSS system this was :file:`/var/log/lockss`, but now there will be a set of subdirectories, one for each component service.

---------------------------
Temporary Storage Directory
---------------------------

:guilabel:`Temporary storage directory:`

Defaults to the content data storage directory. If that directory is remote (e.g. NFS), performance can be improved by supplying a local disk directory here. Do not use a RAM-based ``tmpfs``; in some circumstances a substantial amount of temporary space (tens of GB) may be needed.

------------------
Web user interface
------------------

1. :guilabel:`User name for web UI administration:`

   Enter a username for the primary administrative user in the LOCKSS system's Web user interfaces.

2. :guilabel:`Password for web UI administration user <uiuser>:`

   Enter a password for the primary administrative user.

3. :guilabel:`Password for web UI administration user <uiuser> (again):`

   Re-enter the password for the primary administrative user (if the two passwords do not match, the password will be asked again).

----------------------
Metadata Query Service
----------------------

:guilabel:`Use LOCKSS Metadata Query Service?:`

Enter :kbd:`Y` if you want the metadata query service to be run, otherwise :kbd:`N`.

---------------------------
Metadata Extraction Service
---------------------------

:guilabel:`Use LOCKSS Metadata Extractor Service?:`

Enter :kbd:`Y` if you want the metadata extraction service to be run, otherwise :kbd:`N`.

----------
PostgreSQL
----------

.. |postgres-guilabel| replace:: :guilabel:`Use LOCKSS PostgreSQL DB Service?:`

|postgres-guilabel|

Enter :kbd:`Y` to use the embedded PostgreSQL database (recommended in most cases), or :kbd:`N` if you wish to use an external PostgreSQL database.

*  Enter :kbd:`Y` to use the embedded PostgreSQL database (recommended in most cases). Complete the :ref:`Using the Embedded PostgreSQL Database` section next.

*  Enter :kbd:`N` if you wish to use your own external PostgreSQL database. Complete the :ref:`Using an External PostgreSQL Database` section next.

Using the Embedded PostgreSQL Database
======================================

.. note::

   Complete this section only if you answer :kbd:`Y` to |postgres-guilabel|.

1. :guilabel:`Password for PostgreSQL database:`

   Enter a password for the embedded PostgreSQL database.

2. :guilabel:`Password for PostgreSQL database (again):`

   Re-enter the password for the PostgreSQL database (if the two passwords do not match, the password will be asked again).

3. Complete the :ref:`Solr` section next.

Using an External PostgreSQL Database
=====================================

.. note::

   Complete this section only if you answer :kbd:`N` to |postgres-guilabel|.

1. :guilabel:`Fully qualified hostname (FQDN) of PostgreSQL host:`

   Enter the hostname of your PostgreSQL database, for example :samp:`mypgsql.myuniversity.edu`.

2. :guilabel:`Port used by PostgreSQL host:`

   Enter the port where your running PostgreSQL database can be reached, for example :samp:`5432`.

3. :guilabel:`Login name for PostgreSQL service:`

   Enter the user name for your PostgreSQL database. The default is :samp:`LOCKSS`.

4. :guilabel:`Schema for PostgreSQL service:`

   Enter the schema name to be used by the LOCKSS system. The default is :samp:`LOCKSS`.

5. :guilabel:`Database name prefix for PostgreSQL service:`

   Prefix to use for any LOCKSS databases. The default is :samp:`Lockss` (note the uppercase/lowercase).

6. :guilabel:`Password for PostgreSQL database:`

   Enter the password for your PostgreSQL database.

7. :guilabel:`Password for PostgreSQL database (again):`

   Re-enter the password for your PostgreSQL database (if the two passwords do not match, the password will be asked again).

8. Complete the :ref:`Solr` section next.

----
Solr
----

:guilabel:`Use LOCKSS Solr Service?:`

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

:guilabel:`Use LOCKSS PyWb Service?:`

Enter :kbd:`Y` to use PyWb for content replay; enter :kbd:`N` and you will be offered the option to use OpenWayback instead.

-----------
OpenWayback
-----------

1. :guilabel:`Use LOCKSS OpenWayback Service?:`

   Enter :kbd:`Y` to use OpenWayback for content replay (only if you did not opt for PyWb).

2. :guilabel:`Okay to turn off authentication for read-only requests for LOCKSS Repository Service?:`

   OpenWayback currently does not supply user credentials when reading content from the LOCKSS repository, so the repository must be configured to respond to unauthenticated read requests. Enter :kbd:`Y` to accept this, otherwise OpenWayback will not be enabled.

----------
Conclusion
----------

:guilabel:`OK to store this configuration:`

Enter :kbd:`Y` if the configuration values are to your liking, otherwise :kbd:`N` to make edits.

If you enter :kbd:`Y`, some checks will be run, you may be prompted before the creation of necessary directories, and you will be prompted to run :program:`scripts/start-lockss` to start the configured system.
