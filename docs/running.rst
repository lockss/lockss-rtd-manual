==============
Running LOCKSS
==============

.. note::

   The commands in this section are all run as the ``lockss`` user, in the :ref:`LOCKSS Installer Directory`.

.. index:: ! start-lockss
   single: LOCKSS stack; starting

---------------
Starting LOCKSS
---------------

To start the :term:`LOCKSS stack`, use the :program:`start-lockss` command:

1. If necessary, navigate to the :ref:`LOCKSS Installer Directory` in a ``lockss`` shell, symbolically:

   :samp:`cd {<LOCKSS_INSTALLER_DIRECTORY>}`

2. Run this command as ``lockss``:

   .. code-block:: shell

      scripts/start-lockss

.. index:: start-lockss; options

.. _start-lockss-options:

:program:`start-lockss` accepts some options:

:samp:`--services, -s {SVCS}`
   Start only the configured :ref:`Stack Components` in the semicolon-separated list of component identifiers :samp:`{SVCS}`. By default, the script applies to all configured stack components. See :ref:`Valid Component Identifiers`.

:samp:`--update, -u`
   Force an update of the :term:`containers <container>` of the :term:`LOCKSS stack` from :term:`Docker Hub`, if applicable, before proceeding. This may take several minutes depending on the download speed of the host system.

:samp:`--wait, -w`
   Wait for an internal signal from the system that the its components are initialized. (Currently this internal signal comes from the :ref:`LOCKSS Poller Service`.)

Additional options are available; use :samp:`--help`/:samp:`-h` to see a help message.

.. index:: ! stop-lockss
   single: LOCKSS stack; stopping

---------------
Stopping LOCKSS
---------------

To stop the :term:`LOCKSS stack`, use the :program:`stop-lockss` command:

1. If necessary, navigate to the :ref:`LOCKSS Installer Directory` in a ``lockss`` shell, symbolically:

   :samp:`cd {<LOCKSS_INSTALLER_DIRECTORY>}`

2. Run this command as ``lockss``:

   .. code-block:: shell

      scripts/stop-lockss

:program:`stop-lockss` accepts the :samp:`-s, --services {SVCS}` :index:`option <stop-lockss; options>`. Its argument is a semicolon-separated list that indicates to stop only those configured stack components. See :ref:`Valid Component Identifiers`.

.. index:: restart-lockss, LOCKSS stack; restarting

-----------------
Restarting LOCKSS
-----------------

To restart a running :term:`LOCKSS stack`, use the :program:`restart-lockss` command:

1. If necessary, navigate to the :ref:`LOCKSS Installer Directory` in a ``lockss`` shell, symbolically:

   :samp:`cd {<LOCKSS_INSTALLER_DIRECTORY>}`

2. Run this command as ``lockss``:

   .. code-block:: shell

      scripts/restart-lockss

:program:`restart-lockss` accepts the same :index:`options <restart-lockss; options>` as :program:`start-lockss` (see :ref:`here <start-lockss-options>`).

In particular, :program:`restart-lockss` accepts the :samp:`-s, --services {SVCS}` :index:`option <stop-lockss; options>`. Its argument is a semicolon-separated list that indicates to restart only the given configured stack components (by default, all components are restarted). See :ref:`Valid Component Identifiers`.



----------------------------------
Removing a Configured LOCKSS Stack
----------------------------------

To remove all configurations, volumes and networks configured by the LOCKSS system in Kubernetes, run ``scripts/uninstall-lockss``. This will **not** remove files from the persistent store.

---------------------------
Valid Component Identifiers
---------------------------

:program:`start-lockss`, :program:`restart-lockss`, and :program:`stop-lockss` all accept the :samp:`-s, --services {SVCS}` option, which accepts as its argument a semicolon-separated list of component identifiers, to indicate which configured :ref:`Stack Components` the command applies to. By default, the command applies to all configured components.

The valid stack component identifiers are:

.. list-table::
   :header-rows: 1

   *  *  Component identifier
      *  Component
   *  *  ``configuration``, ``config``, ``cfg``
      *  :ref:`LOCKSS Configuration Service`
   *  *  ``crawler``, ``crawl``
      *  :ref:`LOCKSS Crawler Service`
   *  *  ``metadata``, ``md``
      *  :ref:`LOCKSS Metadata Service`
   *  *  ``openwayback``, ``openwb``, ``owb``
      *  :ref:`OpenWayback`
   *  *  ``poller``, ``poll``, ``pol``
      *  :ref:`LOCKSS Poller Service`
   *  *  ``postgresql``, ``postgres``, ``pgsql``
      *  :ref:`PostgreSQL`
   *  *  ``pywb``
      *  :ref:`Pywb`
   *  *  ``repository``, ``repo``
      *  :ref:`LOCKSS Repository Service`
   *  *  ``soap``
      *  :ref:`LOCKSS SOAP Compatibility Service`
