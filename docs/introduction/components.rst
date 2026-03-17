================
Stack Components
================

.. only:: html and not singlehtml

   .. sidebar::

      .. contents:: Section Table of Contents
         :local:
         :depth: 2
         :backlinks: none

This section presents the various components of |LOCKSS|, their function, and why you might run them as part of your :term:`LOCKSS stack`. When :doc:`/configuring`, the configuration tool will allow you to select which components you wish to run.

--------------------------
Mandatory Stack Components
--------------------------

.. index:: pair: LOCKSS Repository Service; LOCKSS stack

LOCKSS Repository Service
=========================

.. include:: /glossary/lockss-repository-service.rst

By default, it runs a REST API on port 24611 [#fn-ports]_.

.. index:: pair: LOCKSS Configuration Service; LOCKSS stack

LOCKSS Configuration Service
============================

.. include:: /glossary/lockss-configuration-service.rst

By default, it runs a REST API on port 24612 and a Web user interface on port 24602 [#fn-ports]_.

.. index:: pair: LOCKSS Poller Service; LOCKSS stack

LOCKSS Poller Service
=====================

.. include:: /glossary/lockss-poller-service.rst

By default, it runs :term:`LCAP` on port 9729, a REST API on port 24603, and a Web user interface on port 24613 [#fn-ports]_.

.. index:: pair: PostgreSQL; LOCKSS stack

PostgreSQL
==========

|LOCKSS| requires a :term:`PostgreSQL` database to store underlying data, including configuration data, :term:`artifact` indexing data, extracted metadata, and more.

By default, it uses an *embedded PostgreSQL database* [#fn-embedded-postgresql]_ by running a PostgreSQL :term:`container` as part of the :term:`LOCKSS stack`, on port 24620 [#fn-ports]_.

Alternatively, it can be configured to use an *external PostgreSQL database* [#fn-external-postgresql]_ maintained outside the LOCKSS stack.

-------------------------
Optional Stack Components
-------------------------

.. index:: pair: LOCKSS Crawler Service; LOCKSS stack

LOCKSS Crawler Service
======================

.. include:: /glossary/lockss-crawler-service.rst

Out of the box, the LOCKSS Crawler Service ships with the :term:`Classic LOCKSS Crawler`, a mature, highly extensible Web crawler built into |LOCKSS|.

It also includes an API framework for registering external crawlers, and comes with one such external crawler, based on :term:`Wget`.

:term:`LOCKSS plugins <LOCKSS plugin>` are used to control and customize Web harvesting behavior. You may run the LOCKSS Crawler Service as part of your LOCKSS stack if your application of |LOCKSS| involves Web crawling activities.

By default, the LOCKSS Crawler Service runs a REST API on port 24614 and a Web user interface on port 24604 [#fn-ports]_.

.. index:: pair: LOCKSS Metadata Service; LOCKSS stack

LOCKSS Metadata Service
=======================

.. include:: /glossary/lockss-metadata-service.rst

:term:`LOCKSS plugins <LOCKSS plugin>` describe how to extract metadata or other meaning from preserved content, especially content harvested from the Web by the :term:`LOCKSS Crawler Service`. You may run the LOCKSS Metadata Service as part of your LOCKSS stack if your application of |LOCKSS| involves metadata extraction and retrieval activities.

By default, the LOCKSS Metadata Service runs a REST API on port 24615 and a Web user interface on port 24605 [#fn-ports]_.

.. index:: pair: LOCKSS SOAP Compatibility Service; LOCKSS stack

LOCKSS SOAP Compatibility Service
=================================

.. include:: /glossary/lockss-soap-compatibility-service.rst

You may run it as part of your LOCKSS stack if your application of |LOCKSS| involves legacy use of the LOCKSS 1.x SOAP APIs, such as scripting.

By default, it runs a SOAP API on port 24616 [#fn-ports]_.

------------------
Web Replay Engines
------------------

The LOCKSS stack can also run a number of :term:`Web replay engines <Web replay engine>`: :ref:`ServeContent`, :ref:`Pywb`, and :ref:`OpenWayback`.

.. index:: pair: ServeContent; LOCKSS stack

ServeContent
============

.. include:: /glossary/servecontent.rst

Currently, ServeContent is embedded in the :ref:`LOCKSS Poller Service` rather than deployed as a separate :term:`container` in the :term:`LOCKSS stack`.

By default, it runs a Web application on port 24640 [#fn-ports]_.

.. index:: pair: Pywb; LOCKSS stack

Pywb
====

.. include:: /glossary/pywb.rst

By default, it runs a Web application on port 24641 [#fn-ports]_.

.. index:: pair: OpenWayback; LOCKSS stack

OpenWayback
===========

.. include:: /glossary/openwayback.rst

By default, it runs a Web application on port 8080 [#fn-ports]_.

---------------------------
Deprecated Stack Components
---------------------------

As of LOCKSS 2.0-beta2, the :term:`LOCKSS stack` no longer requires a Solr database (embedded or external). Additionally, the LOCKSS Metadata Extraction Service has been merged into the :ref:`LOCKSS Metadata Service`.

----

.. rubric:: Footnotes

.. [#fn-ports]

   See :doc:`/appendix/ports`.

.. [#fn-embedded-postgresql]

   See :ref:`embedded-postgresql-settings`.

.. [#fn-external-postgresql]

   See :ref:`external-postgresql-settings`.
