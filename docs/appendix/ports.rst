=============
Network Ports
=============

.. note::

   Almost all ports changed in LOCKSS 2.0-beta2 compared to LOCKSS 2.0-beta1 and earlier "alpha" versions of LOCKSS 2.0. This can impact firewall rules, custom scripting, and other aspects.

This section describes the default network ports used by the LOCKSS stack.

All ports are TCP in the 24600-24649 range (a subset of 24600-24699 previously), except:

*  The LCAP (LOCKSS audit and repair) port retains its historical value of 9729 [#fn-lcap]_.

*  The OpenWayback port (if in use) is 8080 [#fn-not-configurable]_.

*  The ICP port (if in use) is UDP (noted below as :bdg-primary:`UDP`).

**Important ports are marked in bold.** Unspecified ports in the 24600-24649 range should be considered reserved, although some specific ports are called out as :bdg-danger-line:`reserved for internal use` or :bdg-warning-line:`reserved for future use`.

.. list-table::
   :header-rows: 1

   *  *  Port
      *  Category
      *  Description
      *  Component
   *  *  **8080** [#fn-not-configurable]_
      *  :octicon:`browser` Web replay
      *  OpenWayback Web replay engine
      *  :ref:`OpenWayback`
   *  *  **9729**
      *  :octicon:`shield-check` LCAP
      *  LCAP (LOCKSS audit and repair) port
      *  :ref:`LOCKSS Poller Service`
   *  *  9739
      *  :octicon:`shield-check` LCAP
      *  :bdg-danger-line:`reserved for internal use` (temporary LCAP port [#fn-lcap]_)
      *  :ref:`LOCKSS Poller Service`
   *  *  24600
      *  :octicon:`gear` Web UI
      *  :bdg-warning-line:`reserved for future use` (centralized UI)
      *  
   *  *  24601
      *  :octicon:`gear` Web UI
      *  :bdg-warning-line:`reserved for future use` (repository service UI)
      *  
   *  *  **24602**
      *  :octicon:`gear` Web UI
      *  LOCKSS Configuration Service Web user interface
      *  :ref:`LOCKSS Configuration Service`
   *  *  **24603**
      *  :octicon:`gear` Web UI
      *  LOCKSS Poller Service Web user interface
      *  :ref:`LOCKSS Poller Service`
   *  *  **24604**
      *  :octicon:`gear` Web UI
      *  LOCKSS Crawler Service Web user interface
      *  :ref:`LOCKSS Crawler Service`
   *  *  **24605**
      *  :octicon:`gear` Web UI
      *  LOCKSS Metadata Service Web user interface
      *  :ref:`LOCKSS Metadata Service`
   *  *  24606
      *  :octicon:`gear` Web UI
      *  :bdg-warning-line:`reserved for future use` (SOAP service UI)
      *  
   *  *  24610
      *  :octicon:`terminal` API
      *  :bdg-warning-line:`reserved for future use` (centralized API)
      *  
   *  *  **24611**
      *  :octicon:`terminal` API
      *  LOCKSS Repository Service REST API
      *  :ref:`LOCKSS Repository Service`
   *  *  **24612**
      *  :octicon:`terminal` API
      *  LOCKSS Configuration Service REST API
      *  :ref:`LOCKSS Configuration Service`
   *  *  **24613**
      *  :octicon:`terminal` API
      *  LOCKSS Poller Service REST API
      *  :ref:`LOCKSS Poller Service`
   *  *  **24614**
      *  :octicon:`terminal` API
      *  LOCKSS Crawler Service REST API
      *  :ref:`LOCKSS Crawler Service`
   *  *  **24615**
      *  :octicon:`terminal` API
      *  LOCKSS Metadata Service REST API
      *  :ref:`LOCKSS Metadata Service`
   *  *  **24616**
      *  :octicon:`terminal` API
      *  LOCKSS SOAP Compatibility Service SOAP API
      *  :ref:`LOCKSS SOAP Compatibility Service`
   *  *  24620
      *  :octicon:`stack` Internal
      *  PostgreSQL database
      *  PostgreSQL
   *  *  24621
      *  :octicon:`stack` Internal
      *  ActiveMQ JMS port
      *  :ref:`LOCKSS Configuration Service`
   *  *  24622
      *  :octicon:`stack` Internal
      *  :bdg-warning-line:`reserved for future use` (Solr)
      *  
   *  *  24623
      *  :octicon:`stack` Internal
      *  :bdg-warning-line:`reserved for future use` (HDFS)
      *  
   *  *  **24630**
      *  :octicon:`tools` Content access
      *  Content proxy
      *  :ref:`LOCKSS Poller Service`
   *  *  **24631**
      *  :octicon:`tools` Content access
      *  Audit proxy
      *  :ref:`LOCKSS Poller Service`
   *  *  **24632** :bdg-primary:`UDP`
      *  :octicon:`tools` Content access
      *  ICP server
      *  :ref:`LOCKSS Poller Service`
   *  *  24633
      *  :octicon:`tools` Content access
      *  :bdg-danger-line:`reserved for internal use` (content proxy SSL)
      *  :ref:`LOCKSS Poller Service`
   *  *  24634
      *  :octicon:`tools` Content access
      *  :bdg-danger-line:`reserved for internal use` (audit proxy SSL)
      *  :ref:`LOCKSS Poller Service`
   *  *  **24640**
      *  :octicon:`browser` Web replay
      *  ServeContent Web replay engine and OpenURL resolver
      *  :ref:`LOCKSS Poller Service`
   *  *  **24641**
      *  :octicon:`browser` Web replay
      *  Pywb Web replay engine
      *  Pywb
   *  *  24642
      *  :octicon:`browser` Web replay
      *  :bdg-warning-line:`reserved for future use` (OpenWayback)
      *  

----

.. rubric:: Footnotes

.. [#fn-not-configurable]

   This port is not currently configurable.

.. [#fn-lcap]

   During migration from LOCKSS 1.x to LOCKSS 2.x, a second, temporary LCAP port is in use, by default port 9739.
