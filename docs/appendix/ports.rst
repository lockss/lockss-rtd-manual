=============
Network Ports
=============

.. attention::

   Almost all network ports used in the :term:`LOCKSS stack` changed in |LOCKSS| 2.0-beta2 compared to earlier "alpha" and "beta" versions of LOCKSS 2.0, which impacts :term:`firewall` rules, browser bookmarks, scripts, and more. For example, the port for the Web user interface of the :ref:`LOCKSS Configuration Service`, often used when first logging in LOCKSS in a browser, has moved from 24621 to 24602. See :ref:`LOCKSS 2.0-beta2 Port Changes`.

 See :ref:`LOCKSS 2.0-beta2 Port Changes`.

This section describes the default network ports used by the :term:`LOCKSS stack`.

All ports are TCP in the 24600-24649 range [#fn-subset]_ (with a few exceptions [#fn-exceptions]_), clustered by like purpose, which is correlated with like clients:

.. list-table::
   :header-rows: 1

   *  *  Port range
      *  Category
      *  Clients
   *  *  9729 [#fn-exceptions]_
      *  .. _ports-lcap:
         
         .. |LCAP| replace:: :octicon:`shield-check` :ref:`LCAP port <ports-lcap>`
         
         :octicon:`shield-check` LCAP port
      *  Other nodes participating in the same :term:`LOCKSS network` via :term:`LCAP` (LOCKSS polling and voting)
   *  *  24600-24609
      *  .. _ports-ui:
         
         .. |UI| replace:: :octicon:`gear` :ref:`Web UI <ports-ui>`
         
         :octicon:`gear` Web UI
      *  Administrators of the running LOCKSS stack
   *  *  24610-24619
      *  .. _ports-api:
         
         .. |API| replace:: :octicon:`terminal` :ref:`API <ports-api>`
         
         :octicon:`terminal` API
      *  Other software that integrates with LOCKSS via its APIs
   *  *  24620-24629, also 9739 [#fn-exceptions]_
      *  .. _ports-internal:
         
         .. |INTERNAL| replace:: :octicon:`stack` :ref:`Internal <ports-internal>`
         
         :octicon:`stack` Internal
      *  Internal to the LOCKSS stack (access not expected to be granted to other clients)
   *  *  24630-24639
      *  .. _ports-access:
         
         .. |ACCESS| replace:: :octicon:`file-moved` :ref:`Content access <ports-access>`
         
         :octicon:`file-moved` Content access
      *  Clients who are granted access to the preserved content by way of proxies (including other Web proxies/caches)
   *  *  24640-24649, also 8080 [#fn-exceptions]_
      *  .. _ports-replay:
         
         .. |REPLAY| replace:: :octicon:`browser` :ref:`Web replay <ports-replay>`
         
         :octicon:`browser` Web replay
      *  Clients who are granted access to the preserved content by way of :term:`Web replay <Web replay engine>`

Port by port details are shown below. Unspecified ports below in the 24600-24649 range should be considered reserved, although some ports are specifically called out as :bdg-warning-line:`reserved for future use`.

.. list-table::
   :header-rows: 1

   *  *  Port
      *  Category
      *  Description
      *  Component
   *  *  **8080** [#fn-not-configurable]_
      *  |REPLAY|
      *  OpenWayback Web replay engine
      *  :ref:`OpenWayback`
   *  *  **9729**
      *  |LCAP|
      *  :term:`LCAP` (LOCKSS audit and repair) port
      *  :ref:`LOCKSS Poller Service`
   *  *  9739
      *  |INTERNAL|
      *  :bdg-danger-line:`reserved for internal use` (temporary LCAP port [#fn-lcap]_)
      *  :ref:`LOCKSS Poller Service`
   *  *  *24600*
      *  |UI|
      *  :bdg-warning-line:`reserved for future use` (centralized UI)
      *  
   *  *  *24601*
      *  |UI|
      *  :bdg-warning-line:`reserved for future use` (repository service UI)
      *  
   *  *  **24602**
      *  |UI|
      *  LOCKSS Configuration Service Web user interface
      *  :ref:`LOCKSS Configuration Service`
   *  *  **24603**
      *  |UI|
      *  LOCKSS Poller Service Web user interface
      *  :ref:`LOCKSS Poller Service`
   *  *  **24604**
      *  |UI|
      *  LOCKSS Crawler Service Web user interface
      *  :ref:`LOCKSS Crawler Service`
   *  *  **24605**
      *  |UI|
      *  LOCKSS Metadata Service Web user interface
      *  :ref:`LOCKSS Metadata Service`
   *  *  *24606*
      *  |UI|
      *  :bdg-warning-line:`reserved for future use` (SOAP service UI)
      *  
   *  *  *24610*
      *  |API|
      *  :bdg-warning-line:`reserved for future use` (centralized API)
      *  
   *  *  **24611**
      *  |API|
      *  LOCKSS Repository Service REST API
      *  :ref:`LOCKSS Repository Service`
   *  *  **24612**
      *  |API|
      *  LOCKSS Configuration Service REST API
      *  :ref:`LOCKSS Configuration Service`
   *  *  **24613**
      *  |API|
      *  LOCKSS Poller Service REST API
      *  :ref:`LOCKSS Poller Service`
   *  *  **24614**
      *  |API|
      *  LOCKSS Crawler Service REST API
      *  :ref:`LOCKSS Crawler Service`
   *  *  **24615**
      *  |API|
      *  LOCKSS Metadata Service REST API
      *  :ref:`LOCKSS Metadata Service`
   *  *  **24616**
      *  |API|
      *  LOCKSS SOAP Compatibility Service SOAP API
      *  :ref:`LOCKSS SOAP Compatibility Service`
   *  *  24620
      *  |INTERNAL|
      *  PostgreSQL database
      *  :ref:`PostgreSQL`
   *  *  24621
      *  |INTERNAL|
      *  ActiveMQ JMS port
      *  :ref:`LOCKSS Configuration Service`
   *  *  *24622*
      *  |INTERNAL|
      *  :bdg-warning-line:`reserved for future use` (Solr)
      *  
   *  *  *24623*
      *  |INTERNAL|
      *  :bdg-warning-line:`reserved for future use` (HDFS)
      *  
   *  *  *24629*
      *  |INTERNAL|
      *  :bdg-danger-line:`reserved for internal use` (JMX)
      *  
   *  *  **24630**
      *  |ACCESS|
      *  Content proxy
      *  :ref:`LOCKSS Poller Service`
   *  *  **24631**
      *  |ACCESS|
      *  Audit proxy
      *  :ref:`LOCKSS Poller Service`
   *  *  **24632**
      *  |ACCESS|
      *  :bdg-primary:`UDP` ICP server
      *  :ref:`LOCKSS Poller Service`
   *  *  24633
      *  |ACCESS|
      *  :bdg-danger-line:`reserved for internal use` (content proxy SSL)
      *  :ref:`LOCKSS Poller Service`
   *  *  24634
      *  |ACCESS|
      *  :bdg-danger-line:`reserved for internal use` (audit proxy SSL)
      *  :ref:`LOCKSS Poller Service`
   *  *  **24640**
      *  |REPLAY|
      *  :ref:`ServeContent` Web replay engine and OpenURL resolver
      *  :ref:`LOCKSS Poller Service`
   *  *  **24641**
      *  |REPLAY|
      *  Pywb Web replay engine
      *  :ref:`Pywb`
   *  *  *24642*
      *  |REPLAY|
      *  :bdg-warning-line:`reserved for future use` (OpenWayback)
      *  

-----------------------------
LOCKSS 2.0-beta2 Port Changes
-----------------------------

Almost all network ports used in the :term:`LOCKSS stack` changed in |LOCKSS| 2.0-beta2 compared to earlier "alpha" and "beta" versions of LOCKSS 2.0, which impacts :term:`firewall` rules, browser bookmarks, scripts, and more. The mapping from prior port to current port is shown below.

.. list-table::
   :header-rows: 1

   *  *  Pre-2.0-beta2 Port
      *  2.0-beta2 Port
      *  Category
      *  Description
   *  *  24602
      *  24620
      *  |INTERNAL|
      *  PostgreSQL
   *  *  24603
      *  n/a
      *  |INTERNAL|
      *  Solr (no longer used)
   *  *  24606
      *  24621
      *  |INTERNAL|
      *  ActiveMQ
   *  *  24610
      *  24611
      *  |API|
      *  LOCKSS Repository Service REST API
   *  *  24620
      *  24612
      *  |API|
      *  LOCKSS Configuration Service REST API
   *  *  24621
      *  24602
      *  |UI|
      *  LOCKSS Configuration Service Web UI
   *  *  24630
      *  24613
      *  |API|
      *  LOCKSS Poller Service REST API
   *  *  24631
      *  24603
      *  |UI|
      *  LOCKSS Poller Service Web UI
   *  *  24640
      *  n/a
      *  |API|
      *  LOCKSS Metadata Extraction Service REST API (merged into the LOCKSS Metadata Service)
   *  *  24641
      *  n/a
      *  |UI|
      *  LOCKSS Metadata Extraction Service Web UI (merged into the LOCKSS Metadata Service)
   *  *  24650
      *  24615
      *  |API|
      *  LOCKSS Metadata Service REST API
   *  *  24651
      *  24605
      *  |UI|
      *  LOCKSS Metadata Service Web UI
   *  *  24660
      *  24614
      *  |API|
      *  LOCKSS Crawler Service REST API
   *  *  24661
      *  24604
      *  |UI|
      *  LOCKSS Crawler Service Web UI
   *  *  24670
      *  24630
      *  |ACCESS|
      *  Content proxy
   *  *  24672
      *  24631
      *  |ACCESS|
      *  Audit proxy
   *  *  24674
      *  24632
      *  |ACCESS|
      *  :bdg-primary:`UDP` ICP server
   *  *  24675
      *  24616
      *  |API|
      *  LOCKSS SOAP Compatibility Service SOAP API
   *  *  24680
      *  24640
      *  |REPLAY|
      *  ServeContent
   *  *  24681
      *  24641
      *  |REPLAY|
      *  Pywb

----

.. rubric:: Footnotes

.. [#fn-subset]

   In LOCKSS 2.0-beta1 and "alpha" versions of LOCKSS 2.0, this range was previously 24600-24699.

.. [#fn-exceptions]

   Exceptions include:

   *  The :term:`LCAP` (LOCKSS audit and repair) port retains its historical value of 9729 [#fn-lcap]_.

   *  The :ref:`OpenWayback` port (if in use) is 8080 [#fn-not-configurable]_.

   *  The ICP port (if in use) is UDP (called out as :bdg-primary:`UDP`).

.. [#fn-not-configurable]

   This port is not currently configurable.

.. [#fn-lcap]

   During :doc:`migration from LOCKSS 1.x to 2.x <lockss-portal:migration/index>`, a second, temporary :term:`LCAP` port is in use, by default port 9739.
