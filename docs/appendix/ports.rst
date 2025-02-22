=============
Network Ports
=============

This section describes the default network ports used by the LOCKSS system.

All ports are in the 24600-24699 range, except the LCAP (LOCKSS polling and repair) port which retains its historical value of 9729, and the OpenWayback port which is 8080.

.. note::

   Unless otherwise noted, all ports are **TCP**.

.. list-table::
   :align: center
   :header-rows: 1
   :widths: 10 90

   *  *  **Port**
      *  **Component**
   *  *  8080
      *  OpenWayback Web replay engine
   *  *  9729
      *  LCAP (LOCKSS polling and repair) - :bdg-info-line:`configurable`
   *  *  24600
      *  :bdg-danger-line:`reserved`
   *  *  24602
      *  PostgreSQL
   *  *  24606
      *  ActiveMQ
   *  *  24610
      *  LOCKSS Repository Service - REST port
   *  *  24611
      *  :bdg-danger-line:`reserved`
   *  *  24619
      *  :bdg-danger-line:`reserved`
   *  *  24620
      *  LOCKSS Configuration Service - REST port
   *  *  24621
      *  LOCKSS Configuration Service - UI port
   *  *  24630
      *  LOCKSS Poller Service - REST port
   *  *  24631
      *  LOCKSS Poller Service - UI port
   *  *  24640
      *  LOCKSS Crawler Service - REST port - :bdg-info:`changed in 2.0-beta2`
   *  *  24641
      *  LOCKSS Crawler Service - UI port - :bdg-info:`changed in 2.0-beta2`
   *  *  24650
      *  LOCKSS Metadata Service - REST port
   *  *  24651
      *  LOCKSS Metadata Service - UI port
   *  *  24670
      *  LOCKSS Proxy
   *  *  24671
      *  :bdg-danger-line:`reserved`
   *  *  24672
      *  LOCKSS Audit Proxy
   *  *  24673
      *  :bdg-danger-line:`reserved`
   *  *  24674
      *  ICP server - :bdg-success:`UDP`
   *  *  24675
      *  LOCKSS SOAP Compatibility Service - SOAP port
   *  *  24680
      *  LOCKSS Content Server (ServeContent)
   *  *  24681
      *  Pywb Web replay engine
   *  *  24682
      *  :bdg-danger-line:`reserved`
