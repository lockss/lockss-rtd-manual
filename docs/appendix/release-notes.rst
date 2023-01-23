=============
Release Notes
=============

.. COMMENT LATESTVERSION

--------------------
LOCKSS 2.0.61-alpha6
--------------------

Released: FIXME

.. COMMENT LATESTVERSION

LOCKSS 2.0.61-alpha6 is the first release of the LOCKSS 2.0-alpha6 system.

.. rubric:: Release Notes

*  New SOAP Compatibility Service provides interim backward compatibility for existing SOAP clients. We intend to remove this service once all SOAP clients have been converted to be REST clients.

*  Many of the REST service APIs have changed, to accommodate more usage models (i.e. more typical PLN usage) and to be more consistent. They should now be close to their final form.

*  It is no longer necessary to force all content into the crawled-content model of LOCKSS 1.x.

   *  Content can be directly stored in the LOCKSS repository without the involvement of a staging server or crawler.

   *  The system distinguishes between storing complete HTTP responses (which result from crawls), and plain data files. The audit/repair mechanism works the same for both types of content; the Web replay mechanisms, which involve link rewriting, make sense only for crawled content.

   *  Features for preserving directly-stored content:

      *  No user-defined plugins are needed. The builtin ``NamedPlugin`` and ``NamedArchicalUnit`` are used to group content into archival units.

      * The names of artifacts in ``NamedArchicalUnit``\ s need not be URIs -- they can be arbitrary Unicode strings.

*  LOCKSS 2.x is now binary-compatible with plugins built for LOCKSS 1.x.

*  Memory requirements have been significantly reduced across most services (but are still higher than we would like).

*  Improved robustness in the face of temporary network failures, service restarts, etc.

*  Many of the capabilities needed to migrate content from 1.x to 2.x are present in this release (in conjunction with the 1.76 release of 1.x).

*  **LOCKSS Installer changes**

   *  Add SOAP Compatibility Service

   *  A script is now included to facilitate deleting all content to restore a cluster to its initial state. This is a multi-step operation to make it hard to do accidentally.

   *  Prevent starting new version without running upgrade script if required.

   *  Prevent running upgrade script if stack is still running.

   *  Fix Solr logging.

   *  Adjusted some heap limits.

   *  Allow service-specific JVM flags and port mappings to be specified through environment variables, to support profiling and other uses.

*  **LOCKSS Configuration Service changes**

   *  Added a REST endpoint to calculate AUIDs for non-crawled content.

*  **LOCKSS Repository Service changes**

   *  API changes

      * ``HttpResponse`` and plain resource artifacts are stored and fetched in different formats, natural to each. Internally they are stored in WARC Response records or Resource records, respectively.

      *  Several other cleanups to resolve inconsistencies.

      *  New endpoint to import the individual members of archive files (currently just WARC).

      *  The confusingly-named ``collection`` attribute of ``Artifact`` objects has been renamed ``namespace``.

      *  ``artifactId`` is now ``artifactUuid``.

      *  The Solr schema has changed. Clusters using our embedded Solr database are updated automatically. In the event you are using an external Solr, please contact us (or start over from scratch).

      * AU size information now includes uncompressed size, compressed size and total disk usage.

   *  Performance improvements

      *  Reduced file copies when storing Artifacts.

      *  Reduced lock contention.

      *  Algorithmic improvements to temporary WARC handling to allow garbage collection to run much more frequently, also reducing startup time.

      *  Reduced the number of Solr commits and queries.

      *  Bulk storage mode removes most Solr overhead for migration and reindexing in case of index lossage.

   *  Support for huge filesystems (> 8 EiB).

   *  Bug fixes

      *  Gracefully handle truncated WARCs resulting from abrupt shutdown.

      *  Fixed incorrect character encoding in HTTP headers in WARC response records. (This may cause the headers of ``Artifact``\ s stored with pre-alpha6 releases to not load correctly.)

*  **LOCKSS Poller Service changes**

   * Renamed the REST endpoints that exist only for the interim SOAP Compatibility Service to a distinct path (``/ws``).

*  Building plugins now performs well-formedness checks, similar to 1.x.

*  All changes in LOCKSS `1.75.9 <https://github.com/lockss/lockss-daemon/releases/tag/release-candidate_1-75-b9>`_ and `1.76.5 <https://github.com/lockss/lockss-daemon/releases/tag/release-candidate_1-76-b5>`_.

.. rubric:: Component Versions

.. COMMENT LATESTVERSION

LOCKSS 2.0.61-alpha6 consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.61-alpha6

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.13.0

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.7.0

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.5.0

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.6.0

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.5.0

*  `LOCKSS SOAP Compatibility Service <https://github.com/lockss/laaws-soap-service>`_ version 1.3.0

*  `PostgreSQL <https://www.postgresql.org/>`_ version 9.6.12

*  `Apache Solr <https://solr.apache.org/>`_ version 8.11.2 (custom version 8.11.2-slim-1)

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.4.2 (custom version 2.4.2-3)

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.0 (custom version 2.4.0-5)
