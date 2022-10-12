=============
Release Notes
=============

--------------------
LOCKSS 2.0.43-alpha4
--------------------

| Released: 2021-12-15
| Also known as: LOCKSS 2.0-alpha4c

LOCKSS 2.0.43-alpha4 (also known as LOCKSS 2.0-alpha4c) is a security release and the latest release of the LOCKSS 2.0-alpha4 system. It addresses security vulnerabilities in Apache Log4j 2.x. See :ref:`CVE-2021-45105 and CVE-2021-44832` in our :doc:`security`.

.. rubric:: Release Notes

*  Custom versions of embedded Solr and OpenWayback with Log4j 2.16.0 (CVE-2021-45105).

.. rubric:: Component Versions

LOCKSS 2.0.43-alpha4 consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.43-alpha4

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.5.0

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.11.0

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.4.0

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.3.0

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.3.0

*  `PostgreSQL <https://www.postgresql.org/>`_ version 9.6.12

*  `Apache Solr <https://lucene.apache.org/solr/>`_ version 7.2.1

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.4.2

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.0 (custom version 2.4.0-3)

--------------------
LOCKSS 2.0.42-alpha4
--------------------

| Released: 2021-12-13
| Also known as: LOCKSS 2.0-alpha4b

LOCKSS 2.0.42-alpha4 (also known as LOCKSS 2.0-alpha4b) is a security release of the LOCKSS 2.0-alpha4 system. It addresses security vulnerabilities in Apache Log4j 2.x. See :ref:`CVE-2021-44228, CVE-2021-45046 and CVE-2021-4104` in our :doc:`security`.

.. rubric:: Release Notes

*  Run LOCKSS services, Solr and OpenWayback with Log4j2 mitigation (CVE-2021-44228).

.. rubric:: Component Versions

LOCKSS 2.0.42-alpha4 consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.42-alpha4

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.5.0

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.11.0

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.4.0

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.3.0

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.3.0

*  `PostgreSQL <https://www.postgresql.org/>`_ version 9.6.12

*  `Apache Solr <https://lucene.apache.org/solr/>`_ version 7.2.1

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.4.2

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.0

--------------------
LOCKSS 2.0.41-alpha4
--------------------

| Released: 2021-06-28
| Also known as: LOCKSS 2.0-alpha4a

LOCKSS 2.0.41-alpha4 (also known as LOCKSS 2.0-alpha4a) is the first release of the LOCKSS 2.0-alpha4 system.

.. rubric:: Release Notes

*  Containers are now orchestrated by **K3s**, a lightweight Kubernetes distribution by Kubernetes vendor `Rancher <https://rancher.com/>`_. K3s is compatible with most Linux flavors and comes with a convenient multi-OS installer.

*  Content is now stored in compressed WARC files by default.

*  Numerous bug fixes and enhancements in the repository service and underlying componentry, delivering more reliability and performance in error handling, scalability, and content replay.

*  Many security enhancements, including support for :program:`firewalld` and :program:`ufw`, containers not running as ``root`` internally, the ``lockss`` user no longer needing :program:`sudo` privileges, Solr authentication, and LCAP SSL support with TLSv1.2 by default.

*  Web user interface enhancements, including LCAP SSL key generation and support for the Kubernetes dashboard.

.. rubric:: Component Versions

LOCKSS 2.0.41-alpha4 consists of a configurable set of the following components:

*  `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_ version 2.0.41-alpha4

*  `LOCKSS Configuration Service <https://github.com/lockss/laaws-configservice>`_ version 2.5.0

*  `LOCKSS Repository Service <https://github.com/lockss/laaws-repository-service>`_ version 2.11.0

*  `LOCKSS Metadata Extraction Service <https://github.com/lockss/laaws-metadataextractor>`_ version 2.4.0

*  `LOCKSS Metadata Service <https://github.com/lockss/laaws-metadataservice>`_ version 2.3.0

*  `LOCKSS Poller Service <https://github.com/lockss/laaws-poller>`_ version 2.3.0

*  `PostgreSQL <https://www.postgresql.org/>`_ version 9.6.12

*  `Apache Solr <https://lucene.apache.org/solr/>`_ version 7.2.1

*  `Pywb <https://github.com/webrecorder/pywb>`_ version 2.4.2

*  `OpenWayback <https://github.com/iipc/openwayback>`_ version 2.4.0
