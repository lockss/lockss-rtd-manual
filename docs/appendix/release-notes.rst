=============
Release Notes
=============

.. COMMENT RELEASEDATE

------------------------------------
LOCKSS 2.0.84-beta1 NOT YET RELEASED
------------------------------------

.. caution::

   LOCKSS 2.0.84-beta1 has not been released yet. See the release notes for the latest version: :ref:`latest`.

Released: NOT YET RELEASED

LOCKSS 2.0.84-beta1 NOT YET RELEASED is a bugfix release of LOCKSS 2.0-beta1.

.. rubric:: Release Notes

*  **Features**

   *  Migration from LOCKSS 1.x to 2.x

      *  Removed a bottleneck in the V2 repository that impacts 1.x to 2.x migration.

      *  LCAP message forwarding (for migration) status is displayed in Comm Channels.

   *  User accounts (AccountManager) enabled by default.

   *  Make HashCUS stats human-readable.

*  **Bugs**

   *  Migration from LOCKSS 1.x to 2.x

      *  Fix migration NAT configuration.

      *  Re-enable migrator access to store user accounts.

   *  Ensure repository data connections are closed.

   *  Logging bug in ``CreativeCommonsPermissionChecker``.

   *  Avoid unit test hangs due to entropy starvation.

   *  Check global excludes when following redirects.

   *  Removed unused dependency on obsolete ``json`` version 20140107.

   *  LOCKSS Installer

      *  New error conditions on Debian/Ubuntu with SELinux currently or previously enabled.

      *  Avoid error message if :program:`iptables` is not on the PATH.

      *  Avoid :program:`grep` warning.

.. rubric:: Component Versions

LOCKSS 2.0.84-beta1 NOT YET RELEASED consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.84-beta1

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.15.2

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.9.2

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.7.2

*  `LOCKSS Crawler Service <https://github.com/lockss/laaws-crawler-service>`_ version 1.1.2

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.8.2

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.7.2

*  `LOCKSS SOAP Compatibility Service <https://github.com/lockss/laaws-soap-service>`_ version 1.5.2

*  `PostgreSQL <https://www.postgresql.org/>`_ version 14.7 (14.7-alpine container)

*  `Apache Solr <https://solr.apache.org/>`_ version 8.11.2 (custom 8.11.2-slim-1 container)

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.4.2 (custom 2.4.2-3 container)

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.0 (custom 2.4.0-5 container)

.. _latest:

-------------------
LOCKSS 2.0.83-beta1
-------------------

Released: 2024-09-25

LOCKSS 2.0.83-beta1 is a bugfix release of LOCKSS 2.0-beta1, to fix a problem that caused large temporary files to accumulate on disk.

.. rubric:: Release Notes

*  **Bugs**

   *  Fixed a problem that caused large temporary files to accumulate on disk, potentially filling up the file system.

   *  Resolved an issue that could cause some unit tests to hang.

.. rubric:: Component Versions

LOCKSS 2.0.83-beta1 consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.83-beta1

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.15.1

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.9.1

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.7.1

*  `LOCKSS Crawler Service <https://github.com/lockss/laaws-crawler-service>`_ version 1.1.1

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.8.1

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.7.1

*  `LOCKSS SOAP Compatibility Service <https://github.com/lockss/laaws-soap-service>`_ version 1.5.1

*  `PostgreSQL <https://www.postgresql.org/>`_ version 14.7 (14.7-alpine container)

*  `Apache Solr <https://solr.apache.org/>`_ version 8.11.2 (custom 8.11.2-slim-1 container)

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.4.2 (custom 2.4.2-3 container)

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.0 (custom 2.4.0-5 container)

-------------------
LOCKSS 2.0.82-beta1
-------------------

Released: 2024-08-19

LOCKSS 2.0.82-beta1 is a bugfix release of LOCKSS 2.0-beta1, bringing minor improvements to the LOCKSS Installer.

.. rubric:: Release Notes

*  **Bugs**

   *  Better path normalization during configuration.

   *  Make the Global LOCKSS Network the default, as was the case in LOCKSS 1.x.

   *  Avoid harmless error message when installing the Kubernetes dashboard.

.. rubric:: Component Versions

LOCKSS 2.0.82-beta1 consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.82-beta1

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.15.0

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.9.0

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.7.0

*  `LOCKSS Crawler Service <https://github.com/lockss/laaws-crawler-service>`_ version 1.1.0

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.8.0

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.7.0

*  `LOCKSS SOAP Compatibility Service <https://github.com/lockss/laaws-soap-service>`_ version 1.5.0

*  `PostgreSQL <https://www.postgresql.org/>`_ version 14.7 (14.7-alpine container)

*  `Apache Solr <https://solr.apache.org/>`_ version 8.11.2 (custom 8.11.2-slim-1 container)

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.4.2 (custom 2.4.2-3 container)

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.0 (custom 2.4.0-5 container)

-------------------
LOCKSS 2.0.81-beta1
-------------------

Released: 2024-07-29

LOCKSS 2.0.81-beta1 is the first beta release of the LOCKSS 2.0 system. LOCKSS 2.0-beta1 is now feature-complete compared to LOCKSS 1.x.

.. rubric:: Release Notes

*  **Features**

   *  The major new feature in this release is support for migration from LOCKSS 1.78 to LOCKSS 2.0-beta1. See the :doc:`lockss-portal:migration/index`.

      *  Added a ``--migrate`` option to ``configure-lockss`` to configure LOCKSS 2.0-beta1 for migration from LOCKSS 1.78.

      *  Display warnings on UI elements that should be used cautiously during migration.

      *  Functionality underpinning the migration of configuration data, the copy of databases (PostgreSQL or Derby), and the forwarding of polling traffic and content access requests.

   *  Bumped LCAP protocol minor version for 1.x/2.x compatibility.

   *  Upgraded from Java 8 to Java 17.

      *  Upgraded key dependent libraries to adjust to Java 17, including the Spring framework, XStream.

      *  Switched to the new Doclet framework for Javadoc.

   *  Upgraded REST API specifications and processing to OpenAPI 3, and cleaned up several of the API descriptions.

   *  User account creation is now supported, as in LOCKSS 1.x.

   *  Optional configuration files may now be in XML format (``.xml.opt``).

   * ``start-lockss``, ``stop-lockss``, and ``restart-lockss`` can now start, stop, or restart only selected services, by specifying ``-s "<semicolon-separated-list-of-service-names>"``.

   *  Changed the default values of many configuration parameters to what is appropriate or likely for private LOCKSS networks, rather than the Global LOCKSS Network or CLOCKSS, which simplifies initial PLN setup. See also :doc:`lockss-portal:admin/starter`.

   *  Added the plugin identifier and parent plugins to the PluginReloaded alert.

   *  It is no longer necessary to define the standard titlesets (``AllAus``, ``ActiveAus``, ``InactiveAus``) in the props file. Can be disabled with ``org.lockss.addStandardTitleSets=false``.

   *  Added a CLOCKSS permission statement with open access qualification. Now accepting legacy Creative Commons 2.1, CC0, CERTIFICATION 1.0 and PDM 1.0 licenses.

   *  ``org.lockss.proxy.preferGlobal`` set to ``true`` causes the global proxy setting to override any per-AU proxy setting from the title database. (This is useful in certain testing scenarios.)

*  **Bugs**

   *  Retrieving large files from the repository could cause ``OutOfMemoryError``.

   *  Database connections were not always closed, which could eventually cause hangs when the connection pool was exhausted.

   *  The RIS metadata extractor did not treat ``TY`` tag values case-independently.

   *  Disallowed or disabled servlets return a more appropriate status code (403 or 503).

   *  GenerateLcapKeys omitted the public keystore from the generated zip/tgz.

   *  Files received as repairs in a poll may not have been findable (e.g. by ServeContent) if on a plugin's additional host.

   *  The standard redirection of ``stderr`` output to ``...-logs/stderr.log`` results in truncated output in some startup error scenarios, making it impossible to see the error. This redirection can be disabled by setting the environment variable ``SUPPRESS_STD_REDIR`` to a non-empty string, then the ``stderr`` output will be recorded in the K3s log.

   *  Removed dependency on several internal ``sun.com`` packages.

*  **Performance**

   *  Removed a performance bottleneck recording VoteBlocks during hashing.

*  **Security**

   *  Following best practices, we are removing unnecessary version number disclosures in HTTP responses and UI pages.

.. rubric:: Component Versions

LOCKSS 2.0.81-beta1 consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.81-beta1

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.15.0

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.9.0

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.7.0

*  `LOCKSS Crawler Service <https://github.com/lockss/laaws-crawler-service>`_ version 1.1.0

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.8.0

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.7.0

*  `LOCKSS SOAP Compatibility Service <https://github.com/lockss/laaws-soap-service>`_ version 1.5.0

*  `PostgreSQL <https://www.postgresql.org/>`_ version 14.7 (14.7-alpine container)

*  `Apache Solr <https://solr.apache.org/>`_ version 8.11.2 (custom 8.11.2-slim-1 container)

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.4.2 (custom 2.4.2-3 container)

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.0 (custom 2.4.0-5 container)
