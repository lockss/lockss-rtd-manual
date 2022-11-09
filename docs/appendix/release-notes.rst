=============
Release Notes
=============

--------------------
LOCKSS 2.0.11-alpha1
--------------------

| Released: 2019-05-13
| Also known as: LOCKSS 2.0-alpha1a

LOCKSS 2.0.11-alpha1 (also known as LOCKSS 2.0-alpha1a) is the first release of the LOCKSS 2.0-alpha1 system.

.. rubric:: Release Notes

The LOCKSS 2.0.11-alpha1 release features:

*  Storage in the **LOCKSS Repository Service**, on top of `Solr <https://lucene.apache.org/solr/>`_.

*  Node configuration and state management in the **LOCKSS Configuration Service**.

*  Content ingest with the LOCKSS Crawler.

*  LOCKSS polling and repair with the **LOCKSS Poller Service**.

*  Metadata extraction and query in the **LOCKSS Metadata Extraction Service** and **LOCKSS Metadata Service**, on top of a `Postgres <https://www.postgresql.org/>`_ database.

*  Web replay with LOCKSS ServeContent and `Pywb <https://github.com/webrecorder/pywb>`_, the state-of-the-art Web replay engine behind `Webrecorder <https://webrecorder.io/>`_.

.. rubric:: Component Versions

LOCKSS 2.0.11-alpha1 consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.11-alpha1

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.0.8.0

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.0.1.0

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.0.0.0

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.0.1.0

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.0.0.0

*  `PostgreSQL <https://www.postgresql.org/>`_ version 9.6.12

*  `Apache Solr <https://lucene.apache.org/solr/>`_ version 7.2.1

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.2.20190410 (custom version 2.2.20190410-1)
