=============
Network Ports
=============

This section describes the default network ports used by the LOCKSS system.

All ports are in the 24600-24699 range (246xx), except the LCAP (LOCKSS polling and repair) port which retains its historical value of 9729 (and 9739, used temporarily during migration from LOCKSS 1.x to LOCKSS 2.x), and the OpenWayback port which is 8080.

All ports are configurable, except currently the OpenWayback port (noted below as :bdg-warning-line:`not configurable`).

All ports are TCP, except the ICP port which is UDP (noted below as :bdg-success:`UDP`).

The two ports of the :ref:`LOCKSS Crawler Service` have new default values since LOCKSS 2.0-beta2 (noted below as :bdg-info:`changed in 2.0-beta2`).

All unspecified ports in the 246xx range should be considered reserved (some specific ports are explicitly noted below as :bdg-danger-line:`reserved`).

.. list-table::
   :align: center
   :widths: 10 90
   :header-rows: 1

   *  *  **Port**
      *  **Component**
   *  *  8080
      *  :ref:`OpenWayback` Web replay engine - :bdg-warning-line:`not configurable`
   *  *  9729
      *  :ref:`LOCKSS Poller Service` - LCAP (LOCKSS polling and repair) port
   *  *  9739
      *  :ref:`LOCKSS Poller Service` - Migration LCAP (LOCKSS polling and repair) port, used temporarily during migration from LOCKSS 1.x to LOCKSS 2.x only
   *  *  24600
      *  :bdg-danger-line:`reserved`
   *  *  24602
      *  :ref:`PostgreSQL`
   *  *  24603
      *  :bdg-danger-line:`reserved`
   *  *  24606
      *  ActiveMQ
   *  *  24610
      *  :ref:`LOCKSS Repository Service` - REST port
   *  *  24611
      *  :bdg-danger-line:`reserved`
   *  *  24619
      *  :bdg-danger-line:`reserved`
   *  *  24620
      *  :ref:`LOCKSS Configuration Service` - REST port
   *  *  24621
      *  :ref:`LOCKSS Configuration Service` - UI port
   *  *  24630
      *  :ref:`LOCKSS Poller Service` - REST port
   *  *  24631
      *  :ref:`LOCKSS Poller Service` - UI port
   *  *  24640
      *  :ref:`LOCKSS Crawler Service` - REST port - :bdg-info:`changed in 2.0-beta2`
   *  *  24641
      *  :ref:`LOCKSS Crawler Service` - UI port - :bdg-info:`changed in 2.0-beta2`
   *  *  24650
      *  :ref:`LOCKSS Metadata Service` - REST port
   *  *  24651
      *  :ref:`LOCKSS Metadata Service` - UI port
   *  *  24670
      *  LOCKSS Proxy
   *  *  24671
      *  :bdg-danger-line:`reserved`
   *  *  24672
      *  LOCKSS Audit Proxy
   *  *  24673
      *  :bdg-danger-line:`reserved`
   *  *  24674 :bdg-success:`UDP`
      *  ICP server
   *  *  24675
      *  :ref:`LOCKSS SOAP Compatibility Service` - SOAP port
   *  *  24680
      *  :ref:`ServeContent` (LOCKSS content server)
   *  *  24681
      *  :ref:`Pywb` Web replay engine
   *  *  24682
      *  :bdg-danger-line:`reserved`
