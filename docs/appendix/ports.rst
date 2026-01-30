=============
Network Ports
=============

This section describes the default network ports used by the LOCKSS stack.

**Almost all ports have changed in LOCKSS 2.0-beta2 compared to LOCKSS 2.0-beta1 and earlier "alpha" versions of LOCKSS 2.0.**

All ports are in the 24600-24649 range (a subset of 24600-24699 previously), except the LCAP (LOCKSS audit and repair) port which retains its historical value of 9729 [#fn-lcap]_, and the OpenWayback port which is 8080.

All ports are configurable, except currently the OpenWayback port (noted below as :bdg-warning-line:`not configurable`).

All ports are TCP, except the ICP port which is UDP (noted below as :bdg-success:`UDP port`).

All unspecified ports in the 24600-24649 range should be considered reserved (some specific ports are explicitly noted below as :bdg-danger-line:`reserved`).

.. list-table::
   :header-rows: 1

   *  *  Port
      *  Category
      *  Description
      *  Component
   *  *  8080
      *  Web replay
      *  OpenWayback Web replay engine :bdg-warning-line:`not configurable`
      *  :ref:`OpenWayback`
   *  *  9729
      *  LCAP protocol
      *  LCAP (LOCKSS audit and repair) port
      *  :ref:`LOCKSS Poller Service`
   *  *  9739
      *  LCAP protocol
      *  Temporary LCAP (LOCKSS audit and repair) port [#fn-lcap]_
      *  :ref:`LOCKSS Poller Service`
   *  *  24600
      *  Web UI
      *  :bdg-danger-line:`reserved`
      *  
   *  *  24601
      *  Web UI
      *  :bdg-danger-line:`reserved`
      *  
   *  *  24602
      *  Web UI
      *  LOCKSS Configuration Service Web user interface
      *  :ref:`LOCKSS Configuration Service`
   *  *  24603
      *  Web UI
      *  LOCKSS Poller Service Web user interface
      *  :ref:`LOCKSS Poller Service`
   *  *  24604
      *  Web UI
      *  LOCKSS Crawler Service Web user interface
      *  :ref:`LOCKSS Crawler Service`
   *  *  24605
      *  Web UI
      *  LOCKSS Metadata Service Web user interface
      *  :ref:`LOCKSS Metadata Service`
   *  *  24606
      *  Web UI
      *  :bdg-danger-line:`reserved`
      *  
   *  *  24610
      *  API
      *  :bdg-danger-line:`reserved`
      *  
   *  *  24611
      *  API
      *  LOCKSS Repository Service REST API
      *  :ref:`LOCKSS Repository Service`
   *  *  24612
      *  API
      *  LOCKSS Configuration Service REST API
      *  :ref:`LOCKSS Configuration Service`
   *  *  24613
      *  API
      *  LOCKSS Poller Service REST API
      *  :ref:`LOCKSS Poller Service`
   *  *  24614
      *  API
      *  LOCKSS Crawler Service REST API
      *  :ref:`LOCKSS Crawler Service`
   *  *  24615
      *  API
      *  LOCKSS Metadata Service REST API
      *  :ref:`LOCKSS Metadata Service`
   *  *  24616
      *  API
      *  LOCKSS SOAP Compatibility Service SOAP API
      *  :ref:`LOCKSS SOAP Compatibility Service`
   *  *  24620
      *  Internal
      *  PostgreSQL database
      *  PostgreSQL
   *  *  24621
      *  Internal
      *  ActiveMQ JMS port
      *  :ref:`LOCKSS Configuration Service`
   *  *  24622
      *  Internal
      *  :bdg-danger-line:`reserved`
      *  
   *  *  24623
      *  Internal
      *  :bdg-danger-line:`reserved`
      *  
   *  *  24630
      *  Content access
      *  Content proxy
      *  :ref:`LOCKSS Poller Service`
   *  *  24631
      *  Content access
      *  Audit proxy
      *  :ref:`LOCKSS Poller Service`
   *  *  24632
      *  Content access
      *  ICP server :bdg-success:`UDP port`
      *  :ref:`LOCKSS Poller Service`
   *  *  24640
      *  Web replay
      *  ServeContent Web replay engine and OpenURL resolver
      *  :ref:`LOCKSS Poller Service`
   *  *  24641
      *  Web replay
      *  Pywb Web replay engine
      *  Pywb
   *  *  24642
      *  Web replay
      *  :bdg-danger-line:`reserved`
      *  
   *  *  24643
      *  Web replay
      *  :bdg-danger-line:`reserved`
      *  

----

.. rubric:: Footnotes

.. [#fn-lcap]

   During migration from LOCKSS 1.x to LOCKSS 2.x, a second, temporary LCAP port is in use, by default port 9739.
