=============
Release Notes
=============

.. COMMENT RELEASEDATE

.. _latest:

------------------------------------
LOCKSS 2.0.91-beta2 NOT YET RELEASED
------------------------------------

Released: NOT YET RELEASED

LOCKSS 2.0.91-beta2 NOT YET RELEASED is the second beta release of the LOCKSS 2.0 system.

.. rubric:: Release Notes

*  **Major changes**

   *  The artifact index uses PostgreSQL instead of Solr starting with this release, for much better performance.

   *  Most UI, REST and other port numbers have changed in this release, to simplify firewall configuration. See :numref:`LOCKSS 2.0-beta2 Port Changes` (:ref:`LOCKSS 2.0-beta2 Port Changes`).

   *  A beta version of officially supported Python clients to interact with the LOCKSS 2.x REST APIs is now available for testing.

*  **Repository**

   *  Support adding a specified artifact version.

   *  Allow replacing a specified uncommitted artifact version.

   *  Now using one WARC journal per WARC file.

   *  Bring ``RestLockssRepository``'s ``callBulkOp`` in line with other client calls, and improve tests.

   *  Repository better detects "full disk" errors and reports them to clients, via a 500 or 507 response.

   *  Added repository error injection framework.

   *  Conditionally compress content depending on media type, only if not already compressed, for a configurable set of media types.

   *  Automatically detect situations requiring rebuilding the artifact index.

   *  Support URLs (artifact names) longer than 1024 characters (via a long URL table).

   *  Consolidated the ``/aus/{auid}/artifacts`` endpoint into ``/artifacts``; moved AUID to a query parameter

   *  Revamped paged iterator logic to not hold database connections open.

*  **Metadata**

   *  The LOCKSS Metadata Extraction Service has been merged into the :ref:`LOCKSS Metadata Service`.

*  **Core**

   *  Apply missing non-default AU config params from TDB at AU config time.

   *  Many updated dependencies.

*  **API changes**

   *  Make result pagination more consistent across services and collections.

   *  Improve REST error handling and error responses.

*  **Security**

   *  IP access control lists for admin access and content access are enforced for third-party services (:ref:`PostgreSQL`, :ref:`Pywb`, :ref:`OpenWayback`).

   *  Temporarily relax strict access control to Account Manager endpoints, in order to allow the migrator to migrate user accounts.

   *  Add role-based authorization uniformly to all REST services.

*  **Performance**

   *  Pipelined artifact iterator, primarily to improve hash performance.

   *  Increased buffer size when reading large WARCs.

*  **Web replay**

   *  Pywb and OpenWayback work better thanks to several fixes.

   *  OpenWayback now supplies credentials to the repository.

   *  AU detail page in the UI now links to Pywb and OpenWayback (if they're configured).

*  **Bug fixes**

   *  Endpoints allowing un-credentialed access now grant correct privileges to credentialed clients.

.. rubric:: Component Versions

LOCKSS 2.0.91-beta2 NOT YET RELEASED consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.91-beta2 NOT YET RELEASED

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.16.0

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.10.0

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.8.0

*  `LOCKSS Crawler Service <https://github.com/lockss/laaws-crawler-service>`_ version 1.2.0

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.8.0

*  `LOCKSS SOAP Compatibility Service <https://github.com/lockss/laaws-soap-service>`_ version 1.6.0

*  `PostgreSQL <https://www.postgresql.org/>`_ version 14.7 (14.7-alpine container)

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.8.3 (custom 2.8.3-1 container)

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.1 (unreleased post-2.4.0 build, custom 2.4.1-2 container)
