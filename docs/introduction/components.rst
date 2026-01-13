==================
Service Components
==================

This section presents the various components of LOCKSS |LATEST_MINOR|, their function, and why you would run them as part of your LOCKSS stack.

When :ref:`Configuring the LOCKSS System`, the configuration tool will allow you to select which components you wish to run.

.. only:: html and not singlehtml

   .. contents:: Section Table of Contents
      :local:
      :backlinks: none

-------------------------
LOCKSS Service Components
-------------------------

LOCKSS Repository Service
=========================

The **LOCKSS Repository Service** is responsible for storing data in artifacts (objects). It is a **mandatory** component of a LOCKSS stack.

By default, the LOCKSS Repository Service runs a REST API on port 24610 of your running LOCKSS stack [#fn-ports]_.

LOCKSS Configuration Service
============================

The **LOCKSS Configuration Service** is responsible for acting as the central nervous system of your LOCKSS stack, keeping state data and other information synchronized between system components. It is a **mandatory** component of a LOCKSS stack.

By default, the LOCKSS Configuration Service runs a REST API on port 24620 and a Web user interface on port 24021 of your running LOCKSS stack [#fn-ports]_.

LOCKSS Poller Service
=====================

The **LOCKSS Poller Service** is reponsible for the LOCKSS audit and repair protocol that allows the multiple nodes in the LOCKSS network your stack is configured to be part of to preserve data together. It is a **mandatory** component of a LOCKSS stack.

By default, the LOCKSS Poller Service runs a REST API on port 24630 and a Web user interface on port 24031 of your running LOCKSS stack [#fn-ports]_. Additionally, by default, the LOCKSS audit and repair protocol (otherwise known as the LCAPv3 port or simply the LCAP port) occurs on port 9729.

LOCKSS Crawler Service
======================

In simple use cases, data is stored into the :ref:`LOCKSS Repository Service` using its REST API, and then preserved among the nodes in the LOCKSS network the node is part of by the :ref:`LOCKSS Poller Service` using the LOCKSS audit and repair protocol. The LOCKSS system is also often used to preserve content stored in the repository from being harvested from the Web. The **LOCKSS Crawler Service** manages Web crawls performed by registered Web crawlers. The LOCKSS Crawler Service is an **optional** component of a LOCKSS stack, needed if your application involves Web harvesting activities.

The LOCKSS Crawler Service ships with the Classic LOCKSS Crawler, a mature, highly extensible Web crawler built into the LOCKSS system. It also includes an API framework for registering additional crawlers, and comes with one such external crawler, based on Wget. LOCKSS plugins are used to control Web harvesting behavior and implement custom behavior.

By default, the LOCKSS Crawler Service runs a REST API on port 24640 and a Web user interface on port 24041 of your running LOCKSS stack [#fn-ports]_.

LOCKSS Metadata Service
=======================

LOCKSS plugins can also describe how to extract metadata or other meaning from preserved content, especially content harvested from the Web by the :ref:`LOCKSS Crawler Service`. The **LOCKSS Metadata Service** manages metadata extraction jobs and provides access to extracted metadata through DOI resolution, OpenURL queries and other means. The LOCKSS Metadata Service is an **optional** component of a LOCKSS stack, needed if your application involves metadata extraction and retrieval activities.

By default, the LOCKSS Metadata Service runs a REST API on port 24650 and a Web user interface on port 24051 of your running LOCKSS stack [#fn-ports]_.

LOCKSS SOAP Compatibility Service
=================================

LOCKSS 1.x offered a limited SOAP API. To help with the transition to the more comprehensive LOCKSS 2.x APIs, you can run the **LOCKSS SOAP Compatibility Service** as part of your stack, to offer an endpoint that implements a large subset of the LOCKSS 1.x SOAP API and translate the requests to corresponding LOCKSS 2.x REST API calls, routing them to the appropriate :ref:`LOCKSS Service Components`. This component is **optional**. By default, it runs on port 24675 of your running LOCKSS stack [#fn-ports]_.

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

---------------------
Additional Components
---------------------

.. tip::

   LOCKSS |LATEST_MINOR| no longer requires a Solr database (embedded or external).

PostgreSQL Database
===================

The LOCKSS stack requires a `PostgreSQL <https://www.postgresql.org/>`_ database to store underlying data. This **mandatory** component can be either an **embedded PostgreSQL database** run as part of the LOCKSS stack without having to install and maintain your own, or alternatively, you can configure your LOCKSS stack to use an **external PostgreSQL database** provided and administered by you or your IT department.

By default, the embeeded PostgreSQL database runs on port 24602 of your running LOCKSS stack [#fn-ports]_.

----

.. rubric:: Footnotes

.. [#fn-ports] See :doc:`/appendix/ports`.
