=======================
Troubleshooting CoreDNS
=======================

If both :file:`/etc/resolv.conf` and :file:`/run/systemd/resolve/resolv.conf` (files used to list the IP address of DNS servers) contain loopback addresses, CoreDNS (a component of the K3s Kubernetes cluster that handles DNS resolution) will not work properly [#fnreference]_. If :program:`install-lockss` detects this situation, you will see a warning message and the following prompt [#fninstaller]_:

:guilabel:`IP address(es) of DNS resolvers, separated by ';'`

Enter a semicolon-separated list of DNS server IP addresses that are *not* loopback addresses or hit :kbd:`Enter` to accept the proposed value.

.. tip::

   If the DNS settings of your system change after K3s is initially installed (for example if DNS servers are added or removed), run this command (which is relative to the :ref:`lockss-installer-directory`) as a privileged user who can become ``root`` via :program:`sudo` [#fnprivileged]_:

   .. code-block:: shell

      scripts/install-lockss --configure-coredns

   This will run only the :ref:`Configuring CoreDNS for K3s` phase of :program:`install-lockss`.

----

.. rubric:: Footnotes

.. [#fnreference]

   References:

   *  https://coredns.io/plugins/loop/#troubleshooting-loops-in-kubernetes-clusters

.. [#fninstaller]

   See :ref:`Configuring CoreDNS for K3s`.

.. [#fnprivileged]

   See :doc:`/appendix/privileged`.
