================
Stack Components
================

.. only:: html and not singlehtml

   .. sidebar::

      .. contents:: Section Table of Contents
         :local:
         :depth: 2
         :backlinks: none

This section presents the various components of the :term:`LOCKSS stack`, their function, and why you might run them as part of your stack. When :doc:`/configuring`, the configuration tool will allow you to select which components you wish to run.

-------------------------
LOCKSS Service Components
-------------------------

LOCKSS Repository Service
=========================

.. include:: /glossary/lockss-repository-service.rst

By default, it runs a REST API on port 24611 [#fn-ports]_.

LOCKSS Configuration Service
============================

.. include:: /glossary/lockss-configuration-service.rst

By default, it runs a REST API on port 24612 and a Web user interface on port 24602 [#fn-ports]_.

LOCKSS Poller Service
=====================

.. include:: /glossary/lockss-poller-service.rst

By default, it runs :term:`LCAP` on port 9729, a REST API on port 24603, and a Web user interface on port 24613 [#fn-ports]_.

LOCKSS Crawler Service
======================

.. include:: /glossary/lockss-crawler-service.rst

Out of the box, the LOCKSS Crawler Service ships with the :term:`Classic LOCKSS Crawler`, a mature, highly extensible Web crawler built into :term:`LOCKSS <LOCKSS system>`.

It also includes an API framework for registering external crawlers, and comes with one such external crawler, based on :term:`Wget`.

:term:`LOCKSS plugins <LOCKSS plugin>` are used to control and customize Web harvesting behavior. You may run the LOCKSS Crawler Service as part of your LOCKSS stack if your application of :term:`LOCKSS <LOCKSS system>` involves Web crawling activities.

By default, the LOCKSS Crawler Service runs a REST API on port 24614 and a Web user interface on port 24604 [#fn-ports]_.

LOCKSS Metadata Service
=======================

.. include:: /glossary/lockss-metadata-service.rst

:term:`LOCKSS plugins <LOCKSS plugin>` describe how to extract metadata or other meaning from preserved content, especially content harvested from the Web by the :term:`LOCKSS Crawler Service`. You may run the LOCKSS Metadata Service as part of your LOCKSS stack if your application of :term:`LOCKSS <LOCKSS system>` involves metadata extraction and retrieval activities.

By default, the LOCKSS Metadata Service runs a REST API on port 24615 and a Web user interface on port 24605 [#fn-ports]_.

LOCKSS SOAP Compatibility Service
=================================

.. include:: /glossary/lockss-soap-compatibility-service.rst

You may run it as part of your LOCKSS stack if your application of :term:`LOCKSS <LOCKSS system>` involves legacy use of the LOCKSS 1.x SOAP APIs, such as scripting.

By default, it runs a SOAP API on port 24616 [#fn-ports]_.

------------------
Web Replay Engines
------------------

The LOCKSS stack can also run a number of **Web replay engines**, to allow preserved content that was harvested from the Web by the :ref:`LOCKSS Crawler Service` to be replayed and browsed from preserved copies: :ref:`ServeContent`, :ref:`Pywb`, and :ref:`OpenWayback`. Web replay engines are **optional** components of a LOCKSS stack, needed if Web replay is required by your application.

ServeContent
============

**ServeContent** is the Web replay engine built into the LOCKSS system. In addition to typical link rewriting, the behavior of ServeContent can also be extended by LOCKSS plugins.

Currently, ServeContent is embedded in the :ref:`LOCKSS Poller Service`. It is an **optional** feature that can be switched on or off. By default, it runs on port 24680 of your running LOCKSS stack [#fn-ports]_.

Pywb
====

`Pywb <https://github.com/webrecorder/pywb>`_ (pronounced "pie-W-B") is a sophisticated, open source Web replay engine by Webrecorder. This **optional** component can be run as part of the LOCKSS stack and replay content from the :ref:`LOCKSS Repository Service`. By default, it runs on port 24681 of your running LOCKSS stack [#fn-ports]_.

OpenWayback
===========

`OpenWayback <https://github.com/iipc/openwayback>`_ is an open source Web replay engine by the International Internet Preservation Cnsortium (IIPC). This **optional** component can be run as part of the LOCKSS stack and replay content from the :ref:`LOCKSS Repository Service`. By default, it runs on port 8080 of your running LOCKSS stack [#fn-ports]_.

------------------
Support Components
------------------

.. tip::

   Since LOCKSS 2.0-beta2, LOCKSS no longer requires a `Solr <https://solr.apache.org/>`_ database (embedded or external).



PostgreSQL Database
===================

The LOCKSS stack requires a `PostgreSQL <https://www.postgresql.org/>`_ database to store underlying data. This **mandatory** component can be either an **embedded PostgreSQL database** run as part of the LOCKSS stack without having to install and maintain your own, or alternatively, you can configure your LOCKSS stack to use an **external PostgreSQL database** provided and administered by you or your IT department.

By default, the embeeded PostgreSQL database runs on port 24602 of your running LOCKSS stack [#fn-ports]_.

----

.. rubric:: Footnotes

.. [#fn-ports] See :doc:`/appendix/ports`.
