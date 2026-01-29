=============
Network Ports
=============

This section describes the default network ports used by the LOCKSS stack.

**Almost all ports have changed in LOCKSS 2.0-beta2 compared to LOCKSS 2.0-beta1 and earlier "alpha" versions of LOCKSS 2.0.**

All ports are in the 24600-24649 range (a subset of 24600-24699 previously), except the LCAP (LOCKSS polling and repair) port which retains its historical value of 9729 [#fn-lcap]_, and the OpenWayback port which is 8080.

All ports are configurable, except currently the OpenWayback port (noted below as :bdg-warning-line:`not configurable`).

All ports are TCP, except the ICP port which is UDP (noted below as :bdg-success:`UDP port`).

All unspecified ports in the 24600-24649 range should be considered reserved (some specific ports are explicitly noted below as :bdg-danger-line:`reserved`).

.. list-table::
   :header-rows: 1

   *  *  Port
      *  Category
      *  Component
      *  Description
   *  *  8080
      *  Web replay
      *  :ref:`OpenWayback`
      *  OpenWayback Web replay engine :bdg-warning-line:`not configurable`
   *  *  9729
      *  LCAP protocol
      *  :ref:`LOCKSS Poller Service`
      *  LCAP (LOCKSS audit and repair) port
   *  *  9739
      *  LCAP protocol
      *  :ref:`LOCKSS Poller Service`
      *  Temporary LCAP (LOCKSS audit and repair) port [#fn-lcap]_
   *  *  24600
      *  Web UI
      *  
      *  :bdg-danger-line:`reserved`
   *  *  24601
      *  Web UI
      *  
      *  :bdg-danger-line:`reserved`
   *  *  24602
      *  Web UI
      *  :ref:`LOCKSS Configuration Service`
      *  LOCKSS Configuration Service Web user interface
   *  *  24603
      *  Web UI
      *  :ref:`LOCKSS Poller Service`
      *  LOCKSS Poller Service Web user interface
   *  *  24604
      *  Web UI
      *  :ref:`LOCKSS Crawler Service`
      *  LOCKSS Crawler Service Web user interface
   *  *  24605
      *  Web UI
      *  :ref:`LOCKSS Metadata Service`
      *  LOCKSS Metadata Service Web user interface
   *  *  24606
      *  Web UI
      *  
      *  :bdg-danger-line:`reserved`
   *  *  24610
      *  API
      *  
      *  :bdg-danger-line:`reserved`
   *  *  24611
      *  API
      *  :ref:`LOCKSS Repository Service`
      *  LOCKSS Repository Service REST API
   *  *  24612
      *  API
      *  :ref:`LOCKSS Configuration Service`
      *  LOCKSS Configuration Service REST API
   *  *  24613
      *  API
      *  :ref:`LOCKSS Poller Service`
      *  LOCKSS Poller Service REST API
   *  *  24614
      *  API
      *  :ref:`LOCKSS Crawler Service`
      *  LOCKSS Crawler Service REST API
   *  *  24615
      *  API
      *  :ref:`LOCKSS Metadata Service`
      *  LOCKSS Metadata Service REST API
   *  *  24616
      *  API
      *  :ref:`LOCKSS SOAP Compatibility Service`
      *  LOCKSS SOAP Compatibility Service SOAP API
   *  *  24620
      *  Internal
      *  PostgreSQL
      *  PostgreSQL database
   *  *  24621
      *  Internal
      *  ActiveMQ
      *  ActiveMQ JMS port
   *  *  24622
      *  Internal
      *  
      *  :bdg-danger-line:`reserved`
   *  *  24623
      *  Internal
      *  
      *  :bdg-danger-line:`reserved`
   *  *  24630
      *  Content access
      *  :ref:`LOCKSS Poller Service`
      *  Content proxy
   *  *  24631
      *  Content access
      *  :ref:`LOCKSS Poller Service`
      *  Audit proxy
   *  *  24632
      *  Content access
      *  :ref:`LOCKSS Poller Service`
      *  ICP server :bdg-success:`UDP port`
   *  *  24640
      *  Web replay
      *  :ref:`LOCKSS Poller Service`
      *  ServeContent Web replay engine and OpenURL resolver
   *  *  24641
      *  Web replay
      *  Pywb
      *  Pywb Web replay engine
   *  *  24642
      *  Web replay
      *  
      *  :bdg-danger-line:`reserved`
   *  *  24643
      *  Web replay
      *  
      *  :bdg-danger-line:`reserved`

----

.. rubric:: Footnotes

.. [#fn-lcap]

   During migration from LOCKSS 1.x to LOCKSS 2.x, a second, temporary LCAP port is in use, by default port 9739.
