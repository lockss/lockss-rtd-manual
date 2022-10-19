=============
Release Notes
=============

--------------------
LOCKSS 2.0.34-alpha3
--------------------

| Released: 2021-06-04
| Also known as: LOCKSS 2.0-alpha3d

LOCKSS 2.0.34-alpha3 (also known as LOCKSS 2.0-alpha3d) is a bug fix release and the altest version of the LOCKSS 2.0-alpha3 system. It addresses a bug in the LOCKSS Installer.

.. rubric:: Release Notes

*  Fix previously deleted or renamed files.

.. rubric:: Component Versions

LOCKSS 2.0.34-alpha3 consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.34-alpha3

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.0.10.1

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.0.4.1

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.0.3.1

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.0.2.1

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.0.2.1

*  `PostgreSQL <https://www.postgresql.org/>`_ version 9.6.12

*  `Apache Solr <https://lucene.apache.org/solr/>`_ version 7.2.1

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.4.2 (custom version 2.4.2-1)

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.0 (custom version 2.4.0-1)

--------------------
LOCKSS 2.0.33-alpha3
--------------------

| Released: 2021-01-29
| Also known as: LOCKSS 2.0-alpha3c

LOCKSS 2.0.33-alpha3 (also known as LOCKSS 2.0-alpha3c) is a security release of the LOCKSS 2.0-alpha3 system. It addresses a vulnerability in a dependent code library.

.. rubric:: Release Notes

*  Use components patched to use Jackson-Databind 2.9.10.8 (CVE-2021-20190).

.. rubric:: Component Versions

LOCKSS 2.0.33-alpha3 consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.33-alpha3

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.0.10.1

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.0.4.1

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.0.3.1

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.0.2.1

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.0.2.1

*  `PostgreSQL <https://www.postgresql.org/>`_ version 9.6.12

*  `Apache Solr <https://lucene.apache.org/solr/>`_ version 7.2.1

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.4.2 (custom version 2.4.2-1)

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.0 (custom version 2.4.0-1)

--------------------
LOCKSS 2.0.32-alpha3
--------------------

| Released: 2020-11-09
| Also known as: LOCKSS 2.0-alpha3b

LOCKSS 2.0.32-alpha3 (also known as LOCKSS 2.0-alpha3b) is a bug fix release of the LOCKSS 2.0-alpha3 system. It addresses a bug in the LOCKSS Installer.

.. rubric:: Release Notes

*  Fix for broken multi-volume substitutions.

.. rubric:: Component Versions

LOCKSS 2.0.32-alpha3 consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.32-alpha3

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.0.10.0

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.0.4.0

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.0.3.0

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.0.2.0

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.0.2.0

*  `PostgreSQL <https://www.postgresql.org/>`_ version 9.6.12

*  `Apache Solr <https://lucene.apache.org/solr/>`_ version 7.2.1

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.4.2 (custom version 2.4.2-1)

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.0 (custom version 2.4.0-1)

--------------------
LOCKSS 2.0.31-alpha3
--------------------

| Released: 2020-10-29
| Also known as: LOCKSS 2.0-alpha3a

LOCKSS 2.0.31-alpha3 (also known as LOCKSS 2.0-alpha3a) is the first release of the LOCKSS 2.0-alpha3 system.

.. rubric:: Release Notes

*  The system's `Docker <https://www.docker.com/>`_ containers are now managed by `MicroK8s <https://microk8s.io/>`_, a lightweight `Kubernetes <https://kubernetes.io/>`_ environment by Ubuntu makers Canonical, rather than Docker Swarm.

*  Design and performance improvements to the repository layer, including support for multiple disk storage volumes (in preparation for migrating existing LOCKSS boxes, many of which have multiple disk storage volumes).

*  The `runcluster <https://github.com/lockss/laaws-dev-scripts/tree/master/runcluster>`_ development environment can be used to run a lightweight LOCKSS system from JAR artifacts built locally from the Git codebase or retrieved from Maven Central or Sonatype OSSRH.

*  Infrastructure for building LOCKSS plugins in the LAAWS environment.

*  IP filtering for REST endpoints (similar to IP filtering for the LOCKSS Web user interface).

*  Pywb 2.4.2.

*  Bugfixes and performance improvements throughout the system.

.. rubric:: Component Versions

LOCKSS 2.0.31-alpha3 consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.31-alpha3

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.0.10.0

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.0.4.0

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.0.3.0

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.0.2.0

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.0.2.0

*  `PostgreSQL <https://www.postgresql.org/>`_ version 9.6.12

*  `Apache Solr <https://lucene.apache.org/solr/>`_ version 7.2.1

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.4.2 (custom version 2.4.2-1)

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.0 (custom version 2.4.0-1)
