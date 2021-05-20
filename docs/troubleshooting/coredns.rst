=======================
Troubleshooting CoreDNS
=======================

-----------------
DNS Configuration
-----------------

If both :file:`/etc/resolv.conf` and :file:`/run/systemd/resolve/resolv.conf` (files used to list the IP address of DNS servers) contain loopback addresses, CoreDNS (a component of the K3s Kubernetes cluster that handles DNS resolution) will not work properly [#fn1]_.

The LOCKSS Installer's :program:`install-k3s` script calls another script, :program:`configure-dns`, which detects this situation at the time K3s is being installed, and offers to make this change with the following prompt [#fn2]_:

:guilabel:`IP address(es) of DNS resolvers, separated by ';'`

.. tip::

   If the DNS settings of your system change after K3s is initially installed (for example if DNS servers are added or removed), run this command in the ``lockss`` user's :file:`lockss-installer` directory as a privileged user who can become root via :program:`sudo` [#fnprivileged]_:

   .. code-block:: shell

      scripts/configure-dns

----

.. rubric:: Footnotes

.. [#fn1]

   References:

   * https://coredns.io/plugins/loop/#troubleshooting-loops-in-kubernetes-clusters

.. [#fn2]

   See :doc:`/installing/k3s`.

.. [#fnprivileged]

   See :doc:`/appendix/privileged`.
