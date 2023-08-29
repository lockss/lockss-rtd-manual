=============
Release Notes
=============

.. _latest:

--------------------
LOCKSS 2.0.71-alpha7
--------------------

.. COMMENT RELEASEDATE

Released: 2023-08-29

LOCKSS 2.0.71-alpha7 is the first release of the LOCKSS 2.0-alpha7 system.

.. rubric:: Release Notes

*  **Features**

   *  The major new feature in this release is the LOCKSS Crawler Service, which provides a REST interface to crawling services. This will allow users to integrate external crawlers by defining a Pluggable Crawler Plugin (similar to the way publisher plugins can be defined).  Initially, Wget is supported (along with the classic LOCKSS crawler).

   *  The provided PostgreSQL container is upgraded to version 14.7. The upgrade script converts existing databases by dumping and reloading them. This may take some time for large databases. **It is very important to run the upgrade script.**

   *  ``NamedPlugin`` can now be used for both direct deposit and with pluggable crawlers.

   *  Added ``StartupStatus`` enum to ``ApiStatus`` REST response, allows clients  to determine when AUs are fully started.

   *  Self-generated SSL certificates for admin UI or ServeContent now have 2048-bit keys.

   *  Added Flush Artifact Caches button to DebugPanel to assist with benchmarking repository performance.

   *  ``AuQuery`` Web Services response now includes AU access URLs.

   *  The remaining (deprecated) REST endpoints in service of Web Services queries have been moved to a ``/ws/...`` path.

   *  The AUID is displayed in the AU detail page, and available in metadata index status tables.

   *  Dependency upgrades: Jsoup 1.16.1, Apache Log4J 2.20.0, Apache Commons FileUpload 1.5, Apache Commons Compress 1.23.0, Apache Commons CSV 1.10.0, Apache Commons Codec 1.16.0, Apache Commons IO 2.13.0, Jonix 2023-05, Json-Path 2.8.0, MARC4J 2.9.5, JDBC PostgreSQL client 42.5.0.

*  **Bug fixes**

   *  Improved robustness handling corrupted WARC files (generally caused by abrupt shutdown).

   *  Fixed bug causing most services to periodically reload config files even when not changed.

   *  Reduced spurious undeleted temp files.

   *  Fixed a unicode normalization vulnerability that might have allowed specially crafted bibliographic info in the title DB to cause the UI to misbehave.

   *  Fixed config file precedence problem due to inconsistent/wrong loading order.

   *  Fixed Repository Service startup problem when Solr is not quite ready.

   *  Fixed a bug preventing hash estimate padding from being fully configurable.

   *  Error logs sometimes omitted Timestamp messages.

   *  PostgreSQL logs no longer accumulate forever.

*  **LOCKSS Installer changes**

   *  Now allows the content, state data (including databases), logs, and temporary storage areas to be placed on different devices. We strongly discourage placing the state data and temporary storage areas on network-attached storage such as NFS.

   *  Allows more end-user control over runtime environment and JVM command line (e.g. to change heap size or add profiling or debugging agents).

   *  When reconfiguring the system after an upgrade, it is no longer necessary to see and accept the default for each answer. If :program:`configure-lockss` is invoked in replay mode with the ``-r`` option, all prompts that already have an answer will simply be echoed and the script will proceed to the next prompt. It will be necessary to enter info (or accept the default) only for new prompts added since the previous release.

*  **LOCKSS Repository Service changes**

   *  New endpoints to retrieve artifact data with a streaming response. (The multipart response, still supported, generally precluded    clients streaming data into an application, negatively impacting performance.)

   *  Added ``excludeStatusPattern`` to ``addArtifacts()``, allows skipped artifacts based on HTTP response code in WARC record.

   *  Added duplicate detection to ``addArtifacts()``.

   *  Removed ``isCompressed`` argument from ``addArtifacts``. The repository service now detects whether the archive file is compressed.

   *  Performance improvements in repository to spend less time recalculating AU sizes.

   *  ``getStoreageInfo`` API now only optionally queries Solr index space, as it is quite slow.

*  **Plugin Packager changes**

   *  Plugin key ``plugin_aux_packages`` allows declaration of packages that should in included in the plugin JAR.

   *  Improved plugin validation.

   *  Validation is now also performed after packaging.

*  **Performance**

   *  Substantial reductions in memory requirements.

   *  Eliminated many duplicate strings and other objects.

   *  Periodically clear PDFBox's (monotonically growing) caches.

   *  Improved hashing performance.

   *  Removed a slow Solr call that was causing some UI pages to be very slow.

   *  Reduced extraneous inter-service network traffic. (Unnecessary config file reloading and redundant storing of some state objects.)

   *  Greatly reduced startup time of services that don't need to load the Title DB.

   *  Implemented database connection pooling.

   *  Improved REST connection pooling.

   *  Reduced start script time.

   *  Applied PostgreSQL tuning.

.. rubric:: Component Versions

LOCKSS 2.0.71-alpha7 consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.71-alpha7

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.14.0

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.8.0

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.6.0

*  `LOCKSS Crawler Service <https://github.com/lockss/laaws-crawler-service>`_ version 1.0.0

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.7.0

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.6.0

*  `LOCKSS SOAP Compatibility Service <https://github.com/lockss/laaws-soap-service>`_ version 1.4.0

*  `PostgreSQL <https://www.postgresql.org/>`_ version 14.7

*  `Apache Solr <https://solr.apache.org/>`_ version 8.11.2 (custom version 8.11.2-slim-1)

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.4.2 (custom version 2.4.2-3)

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.0 (custom version 2.4.0-5)
