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

   *  Added repository error injection framework, to facilitate testing.

   *  Conditionally compress content depending on media type, only if not already compressed, for a configurable set of media types.

   *  Automatically detect situations requiring rebuilding the artifact index.

   *  Support URLs (artifact names) longer than 1024 characters (via a long URL table).

   *  Consolidated the ``/aus/{auid}/artifacts`` endpoint into ``/artifacts``; moved AUID to a query parameter

   *  Revamped paged iterator logic to not hold database connections open.

   *  ``ArtifactIndex`` and ``WarcArtifactDataStore`` versioning and upgrade support.

   *  Ensure multiple storage areas are filled evenly.

*  **Metadata**

   *  The LOCKSS Metadata Extraction Service has been merged into the :ref:`LOCKSS Metadata Service`.

*  **Core**

   *  Make the size of the REST client connection pool configurable.

   *  Allow REST client read/connect timeouts to be changed without restart; default read timeout changed to 1 hour.

   *  Apply missing non-default AU config params from TDB at AU config time.

   *  Added ``plugin_allow_start_url_error`` plugin key.

   *  Added ``isKubernetes()`` and ``isRuncluster()`` methods to platform version; disallow blanks in platform version name and handle semantic versions.

   *  Many updated dependencies.

   *  Enabled ``AccountManager`` by default.

   *  Added ``QueryUrlNormalizer``.

   *  Allow permission page redirects to take off-host excursion and return to original host/URL.

   *  Handle ``Content-Encoding: ""`` header as null.

   *  Made ports in the Content Server Options servlet read only (as they are in fact not yet configurable through the UI in LOCKSS 2.x).

   *  Removed ``ConfigParamDescr.InvalidFormatException`` in favor of ``AuParamType.InvalidFormatException``.

*  **API changes**

   *  Make result pagination more consistent across services and collections.

   *  Improve REST error handling and error responses.

   *  Changed configuration service REST endpoint paths: ``normalizeUrl`` to ``normalizeurl``, ``mimeType`` to ``mediatypes``.

   *  Clean up and update API specifications for ``PageInfo``, ``ArtifactPageInfo``, ``AuidPageInfo``, ``AuSize``, ``RepositoryInfo`` (nullable properties, renamed ``resultsPerPage`` to ``itemsInPage``).

   *  Propagated enum changes (``IncludeContentEnum``, ``BulkAuOpEnum``, etc.) from crawler and poller services.

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

   *  Find the first start URL with content for the default replay URL.

   *  Added `requested_disposition` query parameter (ported from lockss-daemon).

   *  Port `ServeContent` rewrite-for-stem-map logic from lockss-daemon.

   *  Added CDX record endpoint improvements.

   * Don't rewrite ``data:`` URLs.

*  **Bug fixes**

   *  Endpoints allowing un-credentialed access now grant correct privileges to credentialed clients.

   *  Ensure proper URL-encoding of query and path args in REST request URLs.

   *  In plugins with alternative permission URLs, a permission fetch failure could mask failure to fetch a required start URL, erroneously allowing a crawl to appear successful even though it had failed.

   *  Ensure all services are notified of relevant config changes via a ``ConfigChanged`` notification.

   * Prevented `ServeContent` and `ViewContent` from sending incorrect (compressed) content length.

   *  Check global excludes when following redirects.

*  **TDB tools**

   *  Add ``titleName`` trait to supplant the title block's name.

   *  Make title sets based on publisher names, not publisher blocks.

   *  Add AU-level DOI and demote title-level DOI.

   *  ``TdbXml`` set of publisher names now reset between multiple segments (e.g. ``--output-dir``).

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
